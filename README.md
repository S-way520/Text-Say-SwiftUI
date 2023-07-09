# Text-Say-SwiftUI
Enter the text and play the text by voice. SwiftUI.
# The first part
![IMG_0271](https://github.com/S-way520/Text-Say-SwiftUI/assets/95877651/3435842d-9a21-4382-88a4-4f1a8c1b5ec6)
# The secod part
Code file 1
```swift
import SwiftUI
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView(TextSay: "Hello world")
        }
    }
}
```
Code file 2
```swift
import SwiftUI
import AVFoundation
struct ContentView: View {
    let speaker = AVSpeechSynthesizer()
    @State var TextSay: String
    var utterance: AVSpeechUtterance {AVSpeechUtterance(string: TextSay)}
    var body: some View {
        HStack {
            TextField("Enter Text", text: $TextSay)
                .multilineTextAlignment(.center)
                .font(.subheadline)
                .textFieldStyle(RoundedBorderTextFieldStyle())
        }
        Button(action: {
            self.playSpeech()
        }) {
            Image(systemName: "play.circle")
                .resizable()
                .frame(width: 50, height: 50)
                .aspectRatio(contentMode: .fit)
                .accentColor(.green)
        }
        .padding(20)
    }
    func playSpeech() {
        self.speaker.speak(self.utterance)
    }
}
```
