# Http And Alamofire
### Motivation 
* 대규모 API 수정을 인해서 통신 규격이 대대적으로 바뀌게 되었고 
* 그에 따라 Http Client Method를 담당해서 만들게 되었다. 

### Response 
```swift
public struct OpenApiResponse<T:Codable>: Codable {

    public var status: Int
    public var message: String
    public var data: T?

    enum CodingKeys: String, CodingKey {
        case status
        case message
        case data
    }
}
```
- API당 http 통신 메소드를 만드는 것은 효율적이지 못하기 때문에 data쪽을 유동적으로 받을 수 있게 만들었다. 

### Http Method With Alamofire 

```swift
  func request<Parameter: Codable, DecodingSturct: Codable>(
           path: OpenApiPath,
           method: HTTPMethod = .post,
           params: Parameter,
           decodeDataType: DecodingSturct.Type
       ) -> Future<DecodingSturct, Error> {
           Future { [weak self] promise in
               // Set Header Info
               let headers = self?.buildHeader(path: path)
               // Set Request URL
               let hostUrl = AppConfigurationStore.loadServerConfigs()?.openApi ?? ServerConfigurationProvider.instance.getServerUrl(key: URL_OPEN_API)
               
               let url = self?.buildURL(path: path)
               
               // Json Serialized & Json Encoding
               guard let serializedParameter = jsonEncoding(parameter: params) else {
                   promise(.failure(genericJsonError.encodingError))
                   return
               }
               
               // Request To Server
               AF.request(
                   url,
                   method: method,
                   parameters: serializedParameter as? Parameters,
                   encoding: JSONEncoding.default,
                   headers: headers
               )
               .validate(statusCode: self?.validResponseRange ?? 200..<300)
               .responseDecodable(of: OpenApiResponseGeneric<DecodingSturct>.self) { response in
                   
                   switch response.result {
                   case .success(_):
                       // Server와 Status 규칙이 정해지면
                       // Status 분기와 범위를 Enum으로 정의하면 된다.
                       // if response.value.status == SERVER_STATE {}
                       
                       guard let value = response.value else {
                           promise(.failure(OpenApiError.unknownError("server data doesn't exist")))
                           return
                       }
                       
                       guard let data = value.data else {
                           promise(.failure(OpenApiError.unknownError("server data doesn't exist")))
                           return
                       }
                       
                       // Send JSon Data
                       promise(.success(data))
                   case .failure(let error):
                       // Send Failure Data With Error
                       promise(.failure(error))
                   }
               }
           }
       }
```
- Response






