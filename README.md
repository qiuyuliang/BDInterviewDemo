# BDInterviewDemo

```objc
NSArray *sourceArray = @[@{
                                 @"id" : @"1",
                                 @"pid" : @"0"
                                 },
                             @{
                                 @"id" : @"2",
                                 @"pid" : @"1"
                                 },
                             @{
                                 @"id" : @"3",
                                 @"pid" : @"2"
                                 },
                             @{
                                 @"id" : @"4",
                                 @"pid" : @"0"
                                 },
                             @{
                                 @"id" : @"5",
                                 @"pid" : @"4"
                                 },
                             @{
                                 @"id" : @"6",
                                 @"pid" : @"2"
                                 },
                             @{
                                 @"id" : @"7",
                                 @"pid" : @"2"
                                 },
                             @{
                                 @"id" : @"8",
                                 @"pid" : @"0"
                                 },
                             @{
                                 @"id" : @"9",
                                 @"pid" : @"5"
                                 },
                             ];
    
    NSArray *result = [self childFromRootID:@"0" sourceArray:sourceArray];
    NSLog(@"result:%@", result);
```

```
- (NSArray *)childFromRootID:(NSString *)pid sourceArray:(NSArray *)dataArray {
    NSMutableArray *array = [NSMutableArray array];
    
    for (NSDictionary *dic in dataArray) {
        if ([dic[@"pid"] isEqualToString:pid]) {
            
            NSMutableDictionary *tempDict = [NSMutableDictionary dictionary];
            tempDict[@"id"] = dic[@"id"];
            
            NSArray *tempArray = [self childFromRootID:tempDict[@"id"] sourceArray:dataArray];
            
            if (tempArray.count > 0) {
                tempDict[@"child"] = tempArray;
            }
            [array addObject:tempDict];
        }
    }
    
    return array;
}
```
