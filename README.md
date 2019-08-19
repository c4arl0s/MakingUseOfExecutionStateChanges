# MakingUseOfExecutionStateChanges
MakingUseOfExecutionStateChanges

- active -> inactive
- inactive - > background
- background -> inactive
- inactive -> Active

![56855170-ef2a8080-68ff-11e9-922b-05378bdca643](https://user-images.githubusercontent.com/24994818/63232402-3ad5a280-c1ed-11e9-9276-923a7d0227eb.png)

# Handling the inective state

- Charge the program into an iphone.

# ViewController.h

``` objective-c
//
//  ViewController.h
//  HandlingTheInactiveState
//
//  Created by Carlos Santiago Cruz on 8/17/19.
//  Copyright © 2019 Carlos Santiago Cruz. All rights reserved.
//

#import <UIKit/UIKit.h>

@interface ViewController : UIViewController

@property (strong, nonatomic) UILabel *label;

@end
```

# ViewController.m

``` objective-c
//
//  ViewController.m
//  HandlingTheInactiveState
//
//  Created by Carlos Santiago Cruz on 8/17/19.
//  Copyright © 2019 Carlos Santiago Cruz. All rights reserved.
//

#import "ViewController.h"

@interface ViewController ()

@end

@implementation ViewController

- (void)viewDidLoad {
    [super viewDidLoad];
    // Do any additional setup after loading the view.
    CGRect bounds = self.view.bounds;
    CGRect labelFrame = CGRectMake(bounds.origin.x, CGRectGetMidY(bounds) - 50,
                                   bounds.size.width, 100);
    self.label = [[UILabel alloc] initWithFrame:labelFrame];
    self.label.font = [UIFont fontWithName:@"Helvetica" size:70];
    self.label.text = @"Bazinga!";
    self.label.textAlignment = NSTextAlignmentCenter;
    self.label.backgroundColor = [UIColor clearColor];
    [self.view addSubview:self.label];
    
    [self rotateLabelDown];
}

- (void)rotateLabelDown
{
    [UIView animateWithDuration:0.5
                     animations:^{
                         self.label.transform = CGAffineTransformMakeRotation(M_PI);
                     }
                     completion:^(BOOL finished){
                         [self rotateLabelUp];
                     }];
}

- (void)rotateLabelUp
{
    [UIView animateWithDuration:0.5
                     animations:^{
                         self.label.transform = CGAffineTransformMakeRotation(0);
                     }
                     completion:^(BOOL finished){
                         [self rotateLabelDown];
                     }];
}

@end
```

![ezgif-2-f459ee7ce95e](https://user-images.githubusercontent.com/24994818/63232364-d9adcf00-c1ec-11e9-8cf6-515213a01d83.gif)

