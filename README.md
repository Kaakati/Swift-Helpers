# Swift Helpers / Extensions
A Useful curated list of Swift 4 Helpers.

#### Add Padding to UITextFeild
```swift
extension UITextField {
    func setLeftPaddingPoints(_ amount:CGFloat){
        let paddingView = UIView(frame: CGRect(x: 0, y: 0, width: amount, height: self.frame.size.height))
        self.leftView = paddingView
        self.leftViewMode = .always
    }
    func setRightPaddingPoints(_ amount:CGFloat) {
        let paddingView = UIView(frame: CGRect(x: 0, y: 0, width: amount, height: self.frame.size.height))
        self.rightView = paddingView
        self.rightViewMode = .always
    }
}

// example
yourTextField.setLeftPaddingPoints(15)
```

#### Tap View to Dismiss Keyboard
```swift
extension UIViewController
{
    /// self.hidekeyboard() will Dismiss Keyboard on ViewTap
    func hideKeyboard()
    {
        let tap: UITapGestureRecognizer = UITapGestureRecognizer(
            target: self,
            action: #selector(UIViewController.dismissKeyboard))
        
        view.addGestureRecognizer(tap)
    }
    
    @objc func dismissKeyboard()
    {
        view.endEditing(true)
    }
}
// example
self.hidekeyboard()
```


#### String Hex Color
```swift
extension UIColor {
    convenience init(hex: String) {
        let scanner = Scanner(string: hex)
        scanner.scanLocation = 0
        
        var rgbValue: UInt64 = 0
        
        scanner.scanHexInt64(&rgbValue)
        
        let r = (rgbValue & 0xff0000) >> 16
        let g = (rgbValue & 0xff00) >> 8
        let b = rgbValue & 0xff
        
        self.init(
            red: CGFloat(r) / 0xff,
            green: CGFloat(g) / 0xff,
            blue: CGFloat(b) / 0xff, alpha: 1
        )
    }
}

// example
let color = UIColor(hex: "FFFFFF")
```


#### Add Left Image to a UIButton
```swift
extension UIButton {
    /// Add image on left view
    func leftImage(image: UIImage) {
        self.setImage(image, for: .normal)
        self.setImage(image, for: .focused)
        self.setImage(image, for: .highlighted)
        self.tintColor = UIColor.Yaqoot.MainColor.Light
        self.imageEdgeInsets = UIEdgeInsets(top: 0, left: 10, bottom: 0, right: image.size.width * 6)
    }
}
```
