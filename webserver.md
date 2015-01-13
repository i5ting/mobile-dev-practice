# 集成webserver


## GCDWebServer

Lightweight GCD based HTTP server for OS X & iOS (includes web based uploader & WebDAV server)

- https://github.com/swisspol/GCDWebServer

## 实现静态webserver

```

 #import <UIKit/UIKit.h>
 #import "AppDelegate.h"
 #import "GCDWebServer.h"

int main(int argc, char * argv[]) {
    @autoreleasepool {
        NSString *bundleFile = [[NSBundle mainBundle] pathForResource:@"znplayer" ofType:@"bundle"];
//        NSString *htmlFile = [bundleFile stringByAppendingPathComponent:@"/index.html"];
    
        
        GCDWebServer* webServer = [[GCDWebServer alloc] init];
        [webServer addGETHandlerForBasePath:@"/" directoryPath:bundleFile indexFilename:nil cacheAge:3600 allowRangeRequests:YES];
        [webServer startWithPort:8001 bonjourName:nil];

        return UIApplicationMain(argc, argv, nil, NSStringFromClass([AppDelegate class]));
    }
}
```

