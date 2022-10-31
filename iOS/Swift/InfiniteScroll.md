# Infinite Scroll
- 회사에서 페이징 관련 기능을 적용한다고 하여 처음으로 ScrollView와 LazyVStack을 사용하여 구현하였다.
- 테스트 결과 List가 여러모로 사용성이 좋지만, List에서 iOS14 버전에서는 기본 List라인을 없애거나 커스텀할 수 없어 LazyVstack을 채택했다.
- 앱의 최소버전이 iOS 15.0이 된다면 Scroll과 LazyVStack을 List로 대체할 생각이다. 

```swift 
    // View Test Code 
    @State private var pageNum: Int = 1
    
            ScrollView {
                    LazyVStack(spacing: 0) {
                        // ProgressView While Fetching
                        if viewModel.isDataFetchig {
                            ProgressView()
                        } else {
                            // Case Data Exist
                            if viewModel.dataList.list.count > 0 {
                                ForEach(viewModel.dataList.list, id: \.id) { history in
                                    VStack(spacing: 0) {
                                        DataViewCell(history: history)
                                    }
                                }
                                /// - Description : 서버의 총 데이터의 갯수와 모델의 리스트의 갯수를 비교하여
                                ///                 서버의 총 데이터의 갯수가 적은 경우 더 받아올 데이터가 있다고 판단한다.
                                ///                 ProgressView가 UI에 노출되었을 때, 다음 페이지의 데이터를 부르는 로직을 호출한다.
                                if viewModel.dataList.totalCount > viewModel.dataList.list.count {
                                    ProgressView()
                                        .onAppear {
                                            viewModel.fetchMore(pageNum: "\(pageNum)")
                                            pageNum += 1
                                        }
                                }
                            } else {
                                // Case No Data
                                // NoDataView()
                            }
                        }
                    }
                }
```

- 상기의 테스트 코드는 View의 테스트 코드이다.
- 하단의 ScrollView의 하단의 ProgressView가 보이면 viewmodel에 있는 fetchmore을 불러오도록 테스트 코드를 작성하였다. 

```swift 
    /// 다음 페이지를 가져오는 메소드
    /// - Parameter pageNum: 서버에 요청할 페이지 번호
    /// - Description: 받아온 response를 메모리 상에 있는 리스트에 append 해준다.
    func fetchMore(pageNum: String) {
        dataRepository.fetch(
            start: modalStartDate,
            end: modalEndDate,
            type: dataType.rawValue,
            pageSize: nil,
            pageNum: pageNum
        )
        .subscribe(on: DispatchQueue.global(qos: .userInteractive))
        .receive(on: DispatchQueue.main)
        .sink { completion in
            switch completion {
            case .finished:
                break
            case .failure(_):
                break
            }
        } receiveValue: { [weak self] response in
            self?.dataList.list.append(contentsOf: response.list)
        }
        .store(in: &subscription)
    }
```
- 서버에 요청할 페이지 번호와 갯수를 정해서 요청을 한다. 
- 서버에서 받은 response를 List에 append 해준다. 

```swift
public struct DataRequest: Codable {
    public var id: String = ""
    public var start: String = ""
    public var end: String = ""
    public var type: String? = nil
    public var pageSize: String? = nil
    public var pageNum: String? = nil
    public init(){}
}
```
- 리퀘스트 파라미터의 구성은 상기와 같다. 

#### Review
- 앞으로도 앱 전반에 적용될 코드이기 때문에 조금 더 테스트가 필요할 것 같다
- iOS 버전이 15.0이상으로 올라가면 List로 바꿔야겠다
- LazyVStack 과 ScrollView는 List와 달리 Row를 재사용하지 않기 때문에 크게 효율이 차이가 나지는 않지만 효율이 떨어진다고 하고
- Apple에서도 지속적으로 List에 파워풀한 기능들을 넣어주고 있기 때문에 추후에는 바꿔야 할 것 같다 
