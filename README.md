# flexidget
Flexible iOS Widget Preview

With this simple SwiftUI extension you can preview your widget on largets & smallest iOS device in the cleanest & fastest way.

Here is the extension:

import SwiftUI
import WidgetKit

    extension View {
    
     func showWidgetPreviews(for family: WidgetFamily) -> some View {
         Group {
             let devices = ["iPhone XS Max", "iPhone SE"]
             ForEach(devices, id:\.self) { device in
                 self
                     .previewContext(WidgetPreviewContext(family: family))
                     .previewDevice(PreviewDevice(rawValue: device))
                     .previewDisplayName(device)
                
                 self
                     .previewContext(WidgetPreviewContext(family: family))
                     .previewDevice(PreviewDevice(rawValue: device))
                     .colorScheme(.dark)
                     .previewDisplayName(device)
              }
          }
       }
    }


It calls like this:

    struct YOURVIEW_Previews: PreviewProvider {
        static var previews: some View {
            YOURVIEW()
                .showWidgetPreviews(for: .systemSmall) // <= here add this at the end of your view
        }
    }



