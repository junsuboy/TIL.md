1. UIImage to jpegData

```swift
let image = UIImage()

// jpeg 압축이 적용됨
let imageData = image.jpegData(compressionQuality: 0.8)
```



2. UIImage to pngData

```swift
let image = UIImage()

// 무손실 데이터가 됨 (압축 x)
let imageData = image.pngData()
```



이 때 다음과 같이 진행한다면 어떻게 될 것인가?

```swift
let a = image.pngData()
let b = image.jpegData(compressionQuality: 0.8)
let aa = UIImage(data: a!)
let bb = UIImage(data: b!)
let aaa = aa?.pngData()
let aaa2 = aa?.jpegData(compressionQuality: 1.0)
let bbb = bb?.pngData()
let bbb2 = bb?.jpegData(compressionQuality: 1.0)

// 상기 변환과정에 따른 용량 변화를 관찰해보자

let a = image.pngData() 													// 1230008
let b = image.jpegData(compressionQuality: 0.8)		// 112028
let aa = UIImage(data: a!)
let bb = UIImage(data: b!)
let aaa = aa?.pngData()														// 1230020
let aaa2 = aa?.jpegData(compressionQuality: 1.0)	// 712717
let bbb = bb?.pngData()														// 915252
let bbb2 = bb?.jpegData(compressionQuality: 1.0)	// 300071
```

