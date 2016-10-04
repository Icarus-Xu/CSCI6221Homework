# Homework #4

##### by Xuenan Xu GWID G26980825
&nbsp;

**1**
```objective-c
// Stack.h
// Definition of Stack
#import <Foundation/Foundation.h>

@interface Stack : NSObject {
@private
    int size;
@private
    int top;
@private
	// arr is the storage of stack
    NSMutableArray *arr;
}
// Default initialization of stack
- (id)init;
// Initialize stack of a fixed size
- (id)initWithSize:(int)size;
// Push a element to the top of stack
- (void)push:(id)element;
// Pop the top element of stack
- (id)pop;
// Tell if the stack is empty
- (BOOL)isEmpty;
@end
```

```objective-c
// Stack.m
// Implementation of Stack
#import "Stack.h"

@implementation Stack
// Default initialization of stack
- (id)init {
	// Try to initialize the parent class - NSObject
    if (self = [super init]) {
		// If parent class is initialized, define arr to a infinite NSMutableArray
        arr = [NSMutableArray array];
		// I use size as a limitation of number of elements in arr, in this case there is no limit so I assigned a non-reachable value to it
        size = -1;
		// I use top as the number of elements in arr, so it shall be 0 by the time of initialization
        top = 0;
    }
    return self;
}
// Initialize stack of a fixed size
- (id)initWithSize:(int)size1 {
	// Try to initialize the parent class - NSObject
    if (self = [super init]) {
		// If parent class is initialized, define arr to a finite NSMutableArray
        arr = [NSMutableArray arrayWithCapacity:(NSUInteger) size1];
		// As there is no actual limitation by the arrayWithCapacity statement, I shall record the size and limit it by myself
        size = size1;
		// Same as above
        top = 0;
    }
    return self;
}
// Push a element to the top of stack
- (void)push:(id)element {
	// Try if the stack is full
    if (top != size) {
		// If not full, simple add the element to the array and update the count
        [arr addObject:element];
        top++;
    } else {
		// If full, print a error message
        NSLog(@"Stack is full, unable to process push(%@).", element);
    }
}
// Pop the top element of stack
- (id)pop {
	// Try if the stack is empty
    if (arr.count != 0) {
		// If not empty, get the last element and remove it from the list, update the count and then return the element
        NSString *lastElement = arr[arr.count - 1];
        [arr removeLastObject];
        top--;
        return lastElement;
    } else {
		// If empty, print a error message
        NSLog(@"Stack is empty, unable to process pop.");
        return nil;
    }
}
// Tell if the stack is empty
- (BOOL)isEmpty {
    return top == 0;
}
@end
```
```objective-c
// main.m
// Usage example of Stack
#import <Foundation/Foundation.h>
#import "Stack.h"

int main(int argc, const char *argv[]) {
    @autoreleasepool {
        NSLog(@"Infinite stack test:");
        // Initialize with infinite size
        Stack *infiniteStack = [[Stack alloc] init];
		// Push 3 element into the stack
        [infiniteStack push:@"6221"];
        [infiniteStack push:@"CSCI"];
        [infiniteStack push:@"Hello"];
		// Pop 3 times and format a string
        NSLog(@"%@ %@ %@", [infiniteStack pop], [infiniteStack pop], [infiniteStack pop]);
		// Check if the stack is empty (yes)
        NSLog(@"%@", [infiniteStack isEmpty] ? @"Stack is empty" : @"Stack isn't empty");
        // Try to pop one more time on a empty stack (will produce an error)
        [infiniteStack pop];

        NSLog(@"\nFinite stack test:");
        // Initialize with finite size
        Stack *finiteStack = [[Stack alloc] initWithSize:2];
		// Push 2 element into the stack
        [finiteStack push:@"6221"];
        [finiteStack push:@"CSCI"];
        // Try to push one more element into a full stack (will produce an error)
        [finiteStack push:@"6221"];
		// Pop 2 times and format a string
        NSLog(@"%@ %@", [finiteStack pop], [finiteStack pop]);
		// Check if the stack is empty (yes)
        NSLog(@"%@", [finiteStack isEmpty] ? @"Stack is empty" : @"Stack isn't empty");
    }

    return 0;
}
```

**2**
```java
public static void main(String[] args) {
        System.out.println("Polymorphism Test: ");
        Polygon triangle = new Triangle();
        Polygon rectangle = new Rectangle();

        draw(triangle);
        draw(rectangle);
    }

    private static void draw(Polygon polygon) {
        polygon.draw();
    }
```
We can see polymorphism through the implement of  `draw(Polygon polygon)`. In this function, the argument is simple `Polygon`, and the `triangle` and `rectangle` are define to be `Polygon`s, but when we run this program we can see the result like this:
```
Polymorphism Test:
Draw a triangle.
Draw a rectangle.
```
It's vividly shown in the result that the abstract `draw()` function in `Polygon` is called by different subclasses of `Polygon`, that is the usage of polymorphism, with the same parent class, call the same function, reach different ends in subclasses.
