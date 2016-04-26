# CrashDemo
自己写代码捕获异常信息,将捕获到的异常信息在下次联网的时候发给后

1)将UncaughtExceptionHandler1.h UncaughtExceptionHandler1.m 文件拖到项目中

2)AppDelegate.m 中

#import "UncaughtExceptionHandler1.h"
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Override point for customization after application launch.
    //调用这个函数就可以收集崩溃信息
    InstallUncaughtExceptionHandler();

    return YES;
}

3)ViewController.m中 [dict setObject:nil forKey:@"kong"];制造崩溃信息

- (void)viewDidLoad {
    [super viewDidLoad];
    // Do any additional setup after loading the view, typically from a nib.
    NSMutableDictionary *dict = [NSMutableDictionary dictionary];
    //这里打开就可以看到控制台输出异常信息
//    [dict setObject:nil forKey:@"kong"];
}

4)异常信息输出

2016-04-26 11:53:53.941 CrashDemo[1758:465788] 异常信息

*** setObjectForKey: object cannot be nil (key: kong)(
    "4   libc++abi.dylib                     0x0000000197e72f44 <redacted> + 16",
    "5   libc++abi.dylib                     0x0000000197e72b10 __cxa_rethrow + 144",
    "6   libobjc.A.dylib                     0x00000001987e4120 objc_exception_rethrow + 44",
    "7   CoreFoundation                      0x0000000183b14d48 CFRunLoopRunSpecific + 552",
    "8   UIKit                               0x00000001892321c8 <redacted> + 460"
)
