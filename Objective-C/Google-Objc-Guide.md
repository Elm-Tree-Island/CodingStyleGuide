# Google Objective-C Style Guide


> Objective-C is a dynamic, object-oriented extension of C. It's designed to be
> easy to use and read, while enabling sophisticated object-oriented design. It
> is the primary development language for applications on OS X and on iOS.
>
> Objective-C是基于C语言的动态化、面向对象程序设计语言。它被设计的易读易使用，同时支持复杂的面向对象程序设计。Objective-C是OS X和iOS应用程序开发的首选语言。
>
> Apple has already written a very good, and widely accepted, [Cocoa Coding
> Guidelines](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html)
> for Objective-C. Please read it in addition to this guide.
>
> 苹果公司已经为Objective-C撰写了优秀且被广泛接受的 [Cocoa开发代码规范](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html)，除本文档外，可以参考上述文档。
>
> The purpose of this document is to describe the Objective-C (and
> Objective-C++) coding guidelines and practices that should be used for iOS and
> OS X code. These guidelines have evolved and been proven over time on other
> projects and teams.
> Open-source projects developed by Google conform to the requirements in this guide.
>
> 本文档用于描述在用于iOS和OS X程序开发时，Objective-C (Objective-C++)语言的代码规范和最佳实践。该规范已经被其他项目和团队广泛使用并被时间验证。Google的开源项目均采用该代码开发规范。
>
> Note that this guide is not an Objective-C tutorial. We assume that the reader
> is familiar with the language. If you are new to Objective-C or need a
> refresher, please read [Programming with
> Objective-C](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/Introduction/Introduction.html).
>
> 注意本文档不是Objective-C语言教程。我们假设读者已经熟知Objective-C开发语言。如果你是Objective-C新人或需要复习该语言，请阅读[Programming with Objective-C](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/Introduction/Introduction.html)。




## 原则（Principles）

### 关注读者，而非作者（Optimize for the reader, not the writer）

> Codebases often have extended lifetimes and more time is spent reading the code
> than writing it. We explicitly choose to optimize for the experience of our
> average software engineer reading, maintaining, and debugging code in our
> codebase rather than the ease of writing said code. For example, when something
> surprising or unusual is happening in a snippet of code, leaving textual hints
> for the reader is valuable.

阅读代码库中的代码的时间往往远大于书写的时间。我们很明确的选择优化普通软件开发工程师对于代码阅读、维护和调试的体验，而不是写出简易（指简陋甚至）的代码。例如，当对于一小段代码会让人感到惊奇或不寻常时（不可奇技淫巧），给读者书写一段文本注释或说明是非常可贵的。

### 保持一致性 （Be consistent）

> When the style guide allows multiple options it is preferable to pick one option
> over mixed usage of multiple options. Using one style consistently throughout a
> codebase lets engineers focus on other (more important) issues. Consistency also
> enables better automation because consistent code allows more efficient
> development and operation of tools that format or refactor code. In many cases,
> rules that are attributed to "Be Consistent" boil down to "Just pick one and
> stop worrying about it"; the potential value of allowing flexibility on these
> points is outweighed by the cost of having people argue over them.

当编码风格规范中提供规范供选择时，选择一种规范要优于多种规范混用。代码库中使用一致的规范，会帮助工程师节省时间，将精力放在其他更重要的事情上（指减少因为编码规范不统一导致的各种误解）。由于一致的代码风格可以高效的开发和使用工具组件，所以，一致性也可以提高自动化程度。在很多场景中，保持一致性可以归结为“（快速）选一个，然后就不要再担心它”，这种选择的灵活性做法，对比花费更多时间争论选择哪种规范来使用，更具潜在价值。

### 与Apple SDKs保持一致（Be consistent with Apple SDKs）

> Consistency with the way Apple SDKs use Objective-C has value for the same
> reasons as consistency within our code base. If an Objective-C feature solves a
> problem that's an argument for using it. However, sometimes language features
> and idioms are flawed, or were just designed with assumptions that are not
> universal. In those cases it is appropriate to constrain or ban language
> features or idioms.

与上面说的保持一致性一样，与苹果Objective-C SDKs保持一致性同样具有价值。如果一个Objective-C的功能特性解决了一个由于参数使用导致的问题。然而，有时语言的特性和惯用语法是有缺陷的，或者本来就被设计的不是通用的。此时，避免或者禁用这些特性或惯用语法往往更好。

### 风格规范要适度（Style rules(编码规范) should pull their weight）

> The benefit of a style rule must be large enough to justify asking engineers to
> remember it. The benefit is measured relative to the codebase we would get
> without the rule, so a rule against a very harmful practice may still have a
> small benefit if people are unlikely to do it anyway. This principle mostly
> explains the rules we don’t have, rather than the rules we do: for example, goto
> contravenes many of the following principles, but is not discussed due to its
> extreme rarity.

编码规范必须被证明足够有益，以便让工程师信服。这些收益是相对于我们拿一个完全没有规范的代码库来对比的，若工程师执行一个非常糟糕的编码规范，也比完全没有规范好一些。这一原则主要解释我们没有的规则，而不是我们已有的规则。例如，goto违反很多下述原则，但我们由于其极其少见，我们在此不讨论。

## 示例 (Example) 

> They say an example is worth a thousand words, so let's start off with an
> example that should give you a feel for the style, spacing, naming, and so on.

> Here is an example header file, demonstrating the correct commenting and spacing
> for an `@interface` declaration.

俗话说，一个例子胜过千言万语，所以我们举个例子，来初步感受一下编码风格、空格空行布局、命名等等编码规范。

下面头文件的例子，演示如何声明一个`@interface`正确的注释及代码空格空行编码风格。

```objectivec 
// GOOD:

#import <Foundation/Foundation.h>

@class Bar;

/**
 * A sample class demonstrating good Objective-C style. All interfaces,
 * categories, and protocols (read: all non-trivial top-level declarations
 * in a header) MUST be commented. Comments must also be adjacent to the
 * object they're documenting.
 */
@interface Foo : NSObject

/** The retained Bar. */
@property(nonatomic) Bar *bar;

/** The current drawing attributes. */
@property(nonatomic, copy) NSDictionary<NSString *, NSNumber *> *attributes;

/**
 * Convenience creation method.
 * See -initWithBar: for details about @c bar.
 *
 * @param bar The string for fooing.
 * @return An instance of Foo.
 */
+ (instancetype)fooWithBar:(Bar *)bar;

/**
 * Initializes and returns a Foo object using the provided Bar instance.
 *
 * @param bar A string that represents a thing that does a thing.
 */
- (instancetype)initWithBar:(Bar *)bar NS_DESIGNATED_INITIALIZER;

/**
 * Does some work with @c blah.
 *
 * @param blah
 * @return YES if the work was completed; NO otherwise.
 */
- (BOOL)doWorkWithBlah:(NSString *)blah;

@end
```

> An example source file, demonstrating the correct commenting and spacing for the
> `@implementation` of an interface.

实现一个`@implementation` 的正确编码规范示例，展示正确的注释和间距（包括空行，回车，空格等）

```objectivec 
// GOOD:

#import "Shared/Util/Foo.h"

@implementation Foo {
  /** The string used for displaying "hi". */
  NSString *_string;
}

+ (instancetype)fooWithBar:(Bar *)bar {
  return [[self alloc] initWithBar:bar];
}

- (instancetype)init {
  // Classes with a custom designated initializer should always override
  // the superclass's designated initializer.
  return [self initWithBar:nil];
}

- (instancetype)initWithBar:(Bar *)bar {
  self = [super init];
  if (self) {
    _bar = [bar copy];
    _string = [[NSString alloc] initWithFormat:@"hi %d", 3];
    _attributes = @{
      @"color" : [UIColor blueColor],
      @"hidden" : @NO
    };
  }
  return self;
}

- (BOOL)doWorkWithBlah:(NSString *)blah {
  // Work should be done here.
  return NO;
}

@end
```



## 命名（Naming）

> Names should be as descriptive as possible, within reason. Follow standard
> [Objective-C naming rules](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html).

命名需要自达意（即看到命名，即可清楚知道代表的意义）且合理，参照[Objective-C naming rules](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html).

> Avoid non-standard abbreviations (including non-standard acronyms and
> initialisms). Don't worry about saving horizontal space as it is far more
> important to make your code immediately understandable by a new reader. For
> example:

禁用非标准缩写（包括非标准首字母缩略词）。 相对节约横向空间来说，对于一个新的读者来说，能够立即理解意义会更为重要，例如：

```objectivec 
// GOOD:

// Good names.
int numberOfErrors = 0;
int completedConnectionsCount = 0;
tickets = [[NSMutableArray alloc] init];
userInfo = [someObject object];
port = [network port];
NSDate *gAppLaunchDate;
```

```objectivec 
// AVOID:

// Names to avoid.
int w;
int nerr;
int nCompConns;
tix = [[NSMutableArray alloc] init];
obj = [someObject object];
p = [network port];
```

> Any class, category, method, function, or variable name should use all capitals
> for acronyms and [initialisms](https://en.wikipedia.org/wiki/Initialism)
> within the name. This follows Apple's standard of using all capitals within a
> name for acronyms such as URL, ID, TIFF, and EXIF.

任何类、扩展、方法、函数或者变量名，简称或者缩略语必须大写。对于名字，可参照苹果缩略语或简称大写字母标准，例如URL, ID, TIFF, EXIF。

> Names of C functions and typedefs should be capitalized and use camel case as
> appropriate for the surrounding code.

C语言函数或者typedef命名须首字母大写，使用驼峰命名方式区分大小写；

### 文件命名（File Names）

> File names should reflect the name of the class implementation that they
> contain—including case.

文件命名须与该文件中实现的类名保持一致，包括大小写；

> Follow the convention that your project uses.
> File extensions should be as follows:

文件扩展名，约定如下：

扩展名（Extension） | 类型（Type） 
--------- | ---------------------------------
.h        | C/C++/Objective-C头文件（C/C++/Objective-C header file） 
.m        | Objective-C（类）实现文件（Objective-C implementation file） 
.mm       | Objective-C++（类）实现文件（Objective-C++ implementation file） 
.cc       | 纯C++实现文件（Pure C++ implementation file） 
.c        | C实现文件（C implementation file） 

> Files containing code that may be shared across projects or used in a large
> project should have a clearly unique name, typically including the project or
> class [prefix](#prefixes).

包含跨工程或者较大工程中共用的代码的文件，必须有一个清晰唯一的名字，一般包括工程或者类名作为前缀。

> File names for categories should include the name of the class being extended,
> like GTMNSString+Utils.h or NSTextView+GTMAutocomplete.h

扩展类的文件名，须包含被扩展类的类名，例如GTMNSString+Utils.h or NSTextView+GTMAutocomplete.h



### 前缀（Prefixes）

> Prefixes are commonly required in Objective-C to avoid naming collisions in a
> global namespace. Classes, protocols, global functions, and global constants
> should generally be named with a prefix that begins with a capital letter
> followed by one or more capital letters or numbers.

前缀被用来避免全局命名空间的命名冲突。类名、协议、全局方法和全局常量命名，要添加前缀，并且首字母大写，后面包含一个或几个数字或大写字母。

> WARNING: Apple reserves two-letter prefixes—see
> [Conventions in Programming with Objective-C](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/Conventions/Conventions.html)—so
> prefixes with a minimum of three characters are considered best practice.

警告：苹果使用两个字母的前缀，参考[Conventions in Programming with Objective-C](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/Conventions/Conventions.html)，所以，建议最好使用最少三个字符的前缀。

```objectivec 
// GOOD:

/** An example error domain. */
extern NSString *GTMExampleErrorDomain;

/** Gets the default time zone. */
extern NSTimeZone *GTMGetDefaultTimeZone(void);

/** An example delegate. */
@protocol GTMExampleDelegate <NSObject>
@end

/** An example class. */
@interface GTMExample : NSObject
@end

```

### 类命名（Class Names）

> Class names (along with category and protocol names) should start as uppercase
> and use mixed case to delimit words.

类命名（连同扩展和协议命名）需要使用首字母大写，大小写混合的方式来界定不同单词。

> Classes and protocols in code shared across multiple applications must have an
> appropriate [prefix](#prefixes) (e.g. GTMSendMessage). Prefixes are recommended,
> but not required, for other classes and protocols.

跨应用使用的类和协议必须使用合适的前缀（例如：GTMSendMessage）。对于其他类和协议，前缀被推荐使用，但不是必须的。

### Category命名（Category Naming ）

> Category names should start with an appropriate [prefix](#prefixes) identifying
> the category as part of a project or open for general use.

Category名要使用合适的前缀，来表明该扩展是某一工程的一部分或可以通用。

> Category source file names should begin with the class being extended followed
> by a plus sign and the name of the category, e.g., `NSString+GTMParsing.h`.
> Methods in a category should be prefixed with a lowercase version of the prefix
> used for the category name followed by an underscore (e.g.,
> `gtm_myCategoryMethodOnAString:`) in order to prevent collisions in
> Objective-C's global namespace.

Category源文件名必须以被扩展类名开头，中间用+号衔接后面的扩展名字，例如：`NSString+GTMParsing.h`。 扩展中的方法以小写的扩展名为前缀，中间用下划线衔接方法名（例如：`gtm_myCategoryMethodOnAString:`），以便避免全局命名范围内的命名冲突。

> There should be a single space between the class name and the opening
> parenthesis of the category.

类名和扩展名的左圆括号之间，须添加一个空格。

```objectivec 
// GOOD:

// UIViewController+GTMCrashReporting.h

/** A category that adds metadata to include in crash reports to UIViewController. */
@interface UIViewController (GTMCrashReporting)

/** A unique identifier to represent the view controller in crash reports. */
@property(nonatomic, setter=gtm_setUniqueIdentifier:) int gtm_uniqueIdentifier;

/** Returns an encoded representation of the view controller's current state. */
- (nullable NSData *)gtm_encodedState;

@end
```

> If a class is not shared with other projects, categories extending it may omit
> name prefixes and method name prefixes.

若类不被其他工程共用，扩展名和方法名可省略前缀。

```objectivec 
// GOOD:

/** This category extends a class that is not shared with other projects. */
@interface XYZDataObject (Storage)
- (NSString *)storageIdentifier;
@end
```

### OC方法命名（Objective-C Method Names）

> Method and parameter names typically start as lowercase and then use mixed case.

方法名和参数名以小写字母开头，中间夹杂大小写。

> Proper capitalization should be respected, including at the beginning of names.

包括首字母命名，可以考虑某些字母大写。

```objectivec 
// GOOD:

+ (NSURL *)URLWithString:(NSString *)URLString;
```

> The method name should read like a sentence if possible, meaning you should
> choose parameter names that flow with the method name. Objective-C method names
> tend to be very long, but this has the benefit that a block of code can almost
> read like prose, thus rendering many implementation comments unnecessary.

方法名应该尽量读起来像一个句子，告诉你这个方法后面应该传入的参数名。Objective-C方法名倾向于非常长，但是这样的好处就是一段block的代码读起来像散文，因此没必要再添加更多注释。

> Use prepositions and conjunctions like "with", "from", and "to" in the second
> and later parameter names only where necessary to clarify the meaning or
> behavior of the method.

只有在有必要说明方法意义或行为时，才在第二个参数名后，使用例如"with", "from", and "to"等介词和连词。

```objectivec 
// GOOD:

- (void)addTarget:(id)target action:(SEL)action;                          // GOOD; no conjunction needed
- (CGPoint)convertPoint:(CGPoint)point fromView:(UIView *)view;           // GOOD; conjunction clarifies parameter
- (void)replaceCharactersInRange:(NSRange)aRange
            withAttributedString:(NSAttributedString *)attributedString;  // GOOD.
```

> A method that returns an object should have a name beginning with a noun
> identifying the object returned:

返回对象的方法名需要以名词开头，以表明返回的对象类型。

```objectivec 
// GOOD:

- (Sandwich *)sandwich;      // GOOD.
```

```objectivec 
// AVOID:

- (Sandwich *)makeSandwich;  // AVOID.
```



> An accessor method should be named the same as the object it's getting, but it
> should not be prefixed with the word `get`. For example:

访问器方法需要和对象的getting方法一致，但不可有`get`前缀。例如：

```objectivec 
// GOOD:

- (id)delegate;     // GOOD.
```

```objectivec 
// AVOID:

- (id)getDelegate;  // AVOID.
```



> Accessors that return the value of boolean adjectives have method names
> beginning with `is`, but property names for those methods omit the `is`.

返回布尔类型的方法，要以`is`为开头，但属性名省略`is`

> Dot notation is used only with property names, not with method names.

点只用于属性获取，不可用于方法调用

```objectivec 
// GOOD:

@property(nonatomic, getter=isGlorious) BOOL glorious;
- (BOOL)isGlorious;

BOOL isGood = object.glorious;      // GOOD.
BOOL isGood = [object isGlorious];  // GOOD.
```

```objectivec 
// AVOID:

BOOL isGood = object.isGlorious;    // AVOID.
```

```objectivec 
// GOOD:

NSArray<Frog *> *frogs = [NSArray<Frog *> arrayWithObject:frog];
NSEnumerator *enumerator = [frogs reverseObjectEnumerator];  // GOOD.
```

```objectivec 
// AVOID: 避免使用.来调用方法

NSEnumerator *enumerator = frogs.reverseObjectEnumerator;    // AVOID.
```

See [Apple's Guide to Naming Methods](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-BCIGIJJF) for more details on Objective-C naming.

These guidelines are for Objective-C methods only. C++ method names continue to
follow the rules set in the C++ style guide.

更多命名相关内容，参考[Apple's Guide to Naming Methods](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-BCIGIJJF)。

以上规范只适用于Objective-C方法，C++方法命名请参考C++命名指南。

### 函数命名（Function Names）

Function names should start with a capital letter and have a capital letter for
each new word (a.k.a. "[camel case](https://en.wikipedia.org/wiki/Camel_case)" or "Pascal case").

函数名要首字母大写，之后使用驼峰命名法。

```objectivec 
// GOOD:

static void AddTableEntry(NSString *tableEntry);
static BOOL DeleteFile(const char *filename);
```

Because Objective-C does not provide namespacing, non-static functions should
have a [prefix](#prefixes) that minimizes the chance of a name collision.

由于Objective-C不支持命名空间，非静态函数要使用前缀，以最大程度减少命名冲突。

```objectivec 
// GOOD:

extern NSTimeZone *GTMGetDefaultTimeZone(void);
extern NSString *GTMGetURLScheme(NSURL *URL);
```

### 变量命名（Variable Names）

> Variable names typically start with a lowercase and use mixed case to delimit
> words.

> Instance variables have leading underscores. File scope or global variables have
> a prefix `g`. For example: `myLocalVariable`, `_myInstanceVariable`,
> `gMyGlobalVariable`.

变量名首字母小写，采用驼峰命名法.

实例变量使用下划线前缀。文件范围或全局变量使用`g`作为前缀。例如`myLocalVariable`, `_myInstanceVariable`, `gMyGlobalVariable`.

#### 一般变量命名（Common Variable Names）

> Readers should be able to infer the variable type from the name, but do not use
> Hungarian notation for syntactic attributes, such as the static type of a
> variable (int or pointer).

代码读者应该能从命名中推导出变量所代表的含义，但是对于句法属性不要使用匈牙利表示法，例如，对于静态变量，不需要加`s`

> File scope or global variables (as opposed to constants) declared outside the
> scope of a method or function should be rare, and should have the prefix g.

声明在方法或函数外的文件作用域变量或全局变量（区别常量）比较少见，应该带有一个前缀`g`

```objectivec 
// GOOD:

static int gGlobalCounter;
```

#### 实例变量（Instance Variables）

> Instance variable names are mixed case and should be prefixed with an
> underscore, like `_usernameTextField`.

示例变量前边以下划线`_`开头，中间但是使用驼峰法区分大小写。

> NOTE: Google's previous convention for Objective-C ivars was a trailing
> underscore. Existing projects may opt to continue using trailing underscores in
> new code in order to maintain consistency within the project codebase.
> Consistency of prefix or suffix underscores should be maintained within each
> class.

注意：Google之前对Objective-C变量的约定是使用尾部下划线。现有工程中，后续开发可能会选择继续使用实例变量尾部带有下划线的方式，以便与之前工程代码保持一致。在每个类中要保持前后缀下划线的一致性。

#### 常量（Constants）

> Constant symbols (const global and static variables and constants created
> with #define) should use mixed case to delimit words.

常量标识符（包括全局常量、静态变量和使用#define定义的常量）需使用驼峰命名；

> Global and file scope constants should have an appropriate [prefix](#prefixes).

全局和文件作用域常量要带有合适的前缀。

```objectivec 
// GOOD:

extern NSString *const GTLServiceErrorDomain;

typedef NS_ENUM(NSInteger, GTLServiceError) {
  GTLServiceErrorQueryResultMissing = -3000,
  GTLServiceErrorWaitTimedOut       = -3001,
};
```

> Because Objective-C does not provide namespacing, constants with external
> linkage should have a prefix that minimizes the chance of a name collision,
> typically like `ClassNameConstantName` or `ClassNameEnumName`.

由于Objective-C不支持命名空间，与外界关联的常量要使用前缀以最大程度避免命名冲突，常用方式例如`ClassNameConstantName` or `ClassNameEnumName`.

> For interoperability with Swift code, enumerated values should have names that
> extend the typedef name:

与Swift有交互的Objective-C代码，枚举值变量要使用自定义类型名作为前缀：

```objectivec 
// GOOD:

typedef NS_ENUM(NSInteger, DisplayTinge) {
  DisplayTingeGreen = 1,
  DisplayTingeBlue = 2,
};
```

> A lowercase k can be used as a standalone prefix for constants of static storage
> duration declared within implementation files:

在实现文件中，小写字母k可以被用来作为声明独立的常量或者静态变量前缀：

```objectivec 
// GOOD:

static const int kFileCount = 12;
static NSString *const kUserKey = @"kUserKey";
```

> NOTE: Previous convention was for public constant names to begin with a
> lowercase k followed by a project-specific [prefix](#prefixes). This practice is
> no longer recommended.

提示：之前约定中，公共常量名使用小写k开头，以作为工程常量特有标识。该方式不再推荐使用。



## 类型和声明（Types and Declarations ）

### 方法声明（Method Declarations）

> As shown in the [example](#Example), the recommended order
> for declarations in an `@interface` declaration are: properties, class methods,
> initializers, and then finally instance methods. The class methods section
> should begin with any convenience constructors.

如示例所示，声明一个 `@interface` 内容的推荐顺序为：属性，类方法，初始化方法，之后实例方法。类方法区域，把[便捷初始化方法](https://zhuanlan.zhihu.com/p/35695874)放在前面。

### 局部变量（Local Variables）

> Declare variables in the narrowest practical scopes, and close to their use.
> Initialize variables in their declarations.

在靠近需要使用该变量的地方声明变量，声明时完成初始化。

```objectivec 
// GOOD:

CLLocation *location = [self lastKnownLocation];
for (int meters = 1; meters < 10; meters++) {
  reportFrogsWithinRadius(location, meters);
}
```

> Occasionally, efficiency will make it more appropriate to declare a variable
> outside the scope of its use. This example declares meters separate from
> initialization, and needlessly sends the lastKnownLocation message each time
> through the loop:

有时出于效率考虑，把变量声明在作用域外更可取。这个例子声明meters变量，并没有初始化，每次循环时，没必要每次都需要对location进行赋值。

```objectivec 
// AVOID:

int meters;                                         // AVOID.
for (meters = 1; meters < 10; meters++) {
  CLLocation *location = [self lastKnownLocation];  // AVOID.
  reportFrogsWithinRadius(location, meters);
}
```

> Under Automatic Reference Counting, strong and weak pointers to Objective-C
> objects are automatically initialized to `nil`, so explicit initialization to
> `nil` is not required for those common cases. However, automatic initialization
> does *not* occur for many Objective-C pointer types, including object pointers
> declared with the `__unsafe_unretained` ownership qualifier and CoreFoundation
> object pointer types. When in doubt, prefer to initialize all Objective-C
> local variables.

使用ARC时，Objective-C对象的强、弱指针会被自动会被初始化为`nil`，所以通常不需要强制初始化为`nil`。然而，包括利用`__unsafe_unretained`声明的变量和CoreFoundation对象指针，很多Objective-C指针类型不会自动完成初始化。 当无法肯定时，建议所有Objective-C局部变量声明时进行初始化。



### 无符号整型 （Unsigned Integers）

> Avoid unsigned integers except when matching types used by system interfaces.

除匹配系统接口调用外，避免使用无符号整型。

> Subtle errors crop up when doing math or counting down to zero using unsigned
> integers. Rely only on signed integers in math expressions except when matching
> NSUInteger in system interfaces.

使用无符号整型进行数学计算或出现倒数为0时，会出现微妙的错误。除匹配系统接口时使用NSUInteger外，数学计算时只使用带符号整型。

```objectivec 
// GOOD:

NSUInteger numberOfObjects = array.count;
for (NSInteger counter = numberOfObjects - 1; counter > 0; --counter)
```

```objectivec 
// AVOID:

for (NSUInteger counter = numberOfObjects - 1; counter > 0; --counter)  // AVOID.
```

> Unsigned integers may be used for flags and bitmasks, though often NS_OPTIONS or
> NS_ENUM will be more appropriate.

尽管推荐使用NS_OPTIONS或NS_ENUM，无符号整型可以被用来作为标志位或位运算掩码。

### 字节宽度可变类型（Types with Inconsistent Sizes)

> Due to sizes that differ in 32- and 64-bit builds, avoid types long, NSInteger,
> NSUInteger, and CGFloat except when matching system interfaces.

由于long，NSInteger，NSUIInteger和CGFloat类型在32位和64位机上字节宽度不同，除必须匹配调用系统接口外，避免使用。

> Types long, NSInteger, NSUInteger, and CGFloat vary in size between 32- and
> 64-bit builds. Use of these types is appropriate when handling values exposed by
> system interfaces, but they should be avoided for most other computations.

long, NSInteger, NSUInteger, and CGFloat类型在32位和64位环境下字节宽度可变。处理系统暴露的数据时，可以使用上述类型，但其他运算，避免使用。

```objectivec 
// GOOD:

int32_t scalar1 = proto.intValue;

int64_t scalar2 = proto.longValue;

NSUInteger numberOfObjects = array.count;

CGFloat offset = view.bounds.origin.x;
```

```objectivec 
// AVOID:

NSInteger scalar2 = proto.longValue;  // AVOID.
```

> File and buffer sizes often exceed 32-bit limits, so they should be declared
> using `int64_t`, not with `long`, `NSInteger`, or `NSUInteger`.

文件或缓存区大小常常超过32位限制，所以应该使用`int64_t`，而不是`long`, `NSInteger`,或 `NSUInteger`。



## 注释（Comments）

> Comments are absolutely vital to keeping our code readable. The following rules
> describe what you should comment and where. But remember: while comments are
> important, the best code is self-documenting. Giving sensible names to types and
> variables is much better than using obscure names and then trying to explain
> them through comments.

注释对于保证代码可读性至关重要。以下规范说明在哪以及如何写注释。但请记住：

> Pay attention to punctuation, spelling, and grammar; it is easier to read
> well-written comments than badly written ones.

注意（注释的）标点、拼写和语法；写的好的注释更易懂。（aka，注释要写的清楚明白，好好说话）

> Comments should be as readable as narrative text, with proper capitalization and
> punctuation. In many cases, complete sentences are more readable than sentence
> fragments. Shorter comments, such as comments at the end of a line of code, can
> sometimes be less formal, but use a consistent style.
> When writing your comments, write for your audience: the next contributor who will need to understand your code. Be generous—the next one may be you!

注释要读起来是叙事文字，需要使用合适的大小写和标点。很多场景中，完整的句子比一段段的文字更易懂。注释要简短，例如一行代码后的注释，可以是非正式的（句子），但请使用一致的风格。

当你写注释时，要为你的读者而写，也就是后面需要读你代码的合作者。要慷慨些，也许他之后读注释的就是你自己。

### 文件注释（File Comments）

> A file may optionally start with a description of its contents.
> Every file may contain the following items, in order:
>
> - License boilerplate if necessary. Choose the appropriate boilerplate for the license used by the project.
> - A basic description of the contents of the file if necessary.

文件头部可以添加该文件的注释说明。文件注释可以包含这些内容，顺序如下：

- 如有必要，添加许可。选择工程使用的合适的许可引用说明
- 文件内容简要说明

> If you make significant changes to a file with an author line, consider deleting
> the author line since revision history already provides a more detailed and
> accurate record of authorship.

如果对具有作者行的文件进行了重大更改，请考虑删除作者行，因为修订历史记录已提供更详细和准确的作者记录。


### 声明注释（Declaration Comments）

> Every non-trivial interface, public and private, should have an accompanying
> comment describing its purpose and how it fits into the larger picture.

每个公开和私有的重要接口，要有附加的注释说明其作用和试用场景。

> Comments should be used to document classes, properties, ivars, functions,
> categories, protocol declarations, and enums.

注释适用于要有文档说明的类、属性、成员变量、方法、扩展、协议声明及枚举。

```objectivec 
// GOOD:

/**
 * A delegate for NSApplication to handle notifications about app
 * launch and shutdown. Owned by the main app controller.
 */
@interface MyAppDelegate : NSObject {
  /**
   * The background task in progress, if any. This is initialized
   * to the value UIBackgroundTaskInvalid.
   */
  UIBackgroundTaskIdentifier _backgroundTaskID;
}

/** The factory that creates and manages fetchers for the app. */
@property(nonatomic) GTMSessionFetcherService *fetcherService;

@end
```

> Doxygen-style comments are encouraged for interfaces as they are parsed by Xcode
> to display formatted documentation. There is a wide variety of Doxygen commands;
> use them consistently within a project.

接口推荐使用Doxygen风格注释，并可以利用xcode将注释原样转化为文档。Doxygen命令很多样，请在工程中保持一致，即使用同一套Doxygen命令

> If you have already described an interface in detail in the comments at the top
> of your file, feel free to simply state, "See comment at top of file for a
> complete description", but be sure to have some sort of comment.

如果在文件顶部已经添加了对接口的详细说明，你可以轻松的指出："请参考文件顶部的完整说明"，但一定要有类似说明，说明一下。

> Additionally, each method should have a comment explaining its function,
> arguments, return value, thread or queue assumptions, and any side effects.
> Documentation comments should be in the header for public methods, or
> immediately preceding the method for non-trivial private methods.

另外，每个方法需要有注释解释其功能、参数、返回值、使用线程假设，以及副作用。文档化注释需要在公开方法的头文件中，或者紧挨着重要的私有方法前。

> Use descriptive form ("Opens the file") rather than imperative form ("Open the
> file") for method and function comments. The comment describes the function; it
> does not tell the function what to do.

对于方法和函数的注释使用描述性形式，而不是使用命令形式。注释描述其功能，而不是让函数去做什么。

> Document the thread usage assumptions the class, properties, or methods make, if
> any. If an instance of the class can be accessed by multiple threads, take extra
> care to document the rules and invariants surrounding multithreaded use.

对于类、属性、方法，如果需要，添加线程使用假设文档说明。若类的示例被多个线程访问使用，对此文档中要格外说明其在多线程中使用规范及不变式。

> Any sentinel values for properties and ivars, such as `NULL` or `-1`, should be
> documented in comments.

任何属性或成员变量的临界值，例如`NULL`或`-1`, 都需要在文档中注释说明其代表的意义。

> Declaration comments explain how a method or function is used. Comments
> explaining how a method or function is implemented should be with the
> implementation rather than with the declaration.

声明注释用于解释方法或函数应该如何被使用。那些解释方法或函数是如何实现的注释，应该添加在实现处，而不是函数或方法的声明处。

### 实现注释（Implementation Comments）

> Provide comments explaining tricky, subtle, or complicated sections of code.

对刁钻、微妙或复杂的代码添加注释，解释其中奥妙。

```objectivec 
// GOOD:

// Set the property to nil before invoking the completion handler to
// avoid the risk of reentrancy leading to the callback being
// invoked again.
CompletionHandler handler = self.completionHandler;
self.completionHandler = nil;
handler();
```

> When useful, also provide comments about implementation approaches that were
> considered or abandoned.

如果需要，也对一些考虑使用或放弃使用的方法实现添加注释。

> End-of-line comments should be separated from the code by at least 2 spaces. If
> you have several comments on subsequent lines, it can often be more readable to
> line them up.

跟在代码行尾的注释需要至少用两个空格隔开代码与注释。如果你在随后的多行里有多个注释，更易读的办法是把他们（对齐）排好。

```objectivec 
// GOOD:

[self doSomethingWithALongName];  // Two spaces before the comment.
[self doSomethingShort];          // More spacing to align the comment.
```

### 消除符号歧义（Disambiguating Symbols）

> Where needed to avoid ambiguity, use backticks or vertical bars to quote
> variable names and symbols in comments in preference to using quotation marks
> or naming the symbols inline.

在需要避免歧义的地方，使用反引号或竖杠将注释中变量名字或符号引起来，要优于使用引号或内联命名符号。

> In Doxygen-style comments, prefer demarcating symbols with a monospace text
> command, such as `@c`.

在Doxygen风格注释中，更建议使用等宽文本命令来划分标定符号，例如`@c`。

> Demarcation helps provide clarity when a symbol is a common word that might make
> the sentence read like it was poorly constructed. A common example is the symbol
> `count`:

当一个符号命名是常用单词时，划定边界会使注释更清晰。若不划分，可能会使句子读起来不通顺。常见的例子如单词`count`：

```objectivec 
// GOOD:

// Sometimes `count` will be less than zero.
```

> or when quoting something which already contains quotes

或引用已经有引号的文字

```objectivec 
// GOOD:

// Remember to call `StringWithoutSpaces("foo bar baz")`
```

> Backticks or vertical bars are not needed when a symbol is self-apparent.

对于显而易见的文字不需要添加反引号或竖杠。

```objectivec 
// GOOD:

// This class serves as a delegate to GTMDepthCharge.
```

> Doxygen formatting is also suitable for identifying symbols.

Doxygen格式化同样适用标识符号。

```objectivec 
// GOOD:

/** @param maximum The highest value for @c count. */
```

### 对象所有权（Object Ownership）

> For objects not managed by ARC, make the pointer ownership model as explicit as
> possible when it falls outside the most common Objective-C usage idioms.

不在ARC管理下的对象，当这些对象的指针在常见的Objective-C常用用法之外时，需要尽可能明确的说明该对象的指针。

#### MRC（Manual Reference Counting）

> Instance variables for NSObject-derived objects are presumed to be retained; if
> they are not retained, they should be either commented as weak or declared with
> the `__weak` lifetime qualifier.

NSObject子类的所有示例对象都被假定为会被保留计数，若他们没有被保留计数，要么需要注释为弱引用，要么声明时使用为`__weak`标识符。

> An exception is in Mac software for instance variables labeled as `@IBOutlets`,
> which are presumed to not be retained.

在Mac软件中，被标示为 `@IBOutlets`的实例变量是个例外，这些变量假定不会被保留计数。

> Where instance variables are pointers to Core Foundation, C++, and other
> non-Objective-C objects, they should always be declared with strong and weak
> comments to indicate which pointers are and are not retained. Core Foundation
> and other non-Objective-C object pointers require explicit memory management,
> even when building for automatic reference counting.

当实例变量指向Core Foundation，C++或其他非Objective-C对象，这些变量应该使用使用strong和weak，注释其哪些是被保留的，哪些不保留。Core Foundation和其他非Objective-C对象指针需要清晰明确的内存管理，即便使用ARC情况下也一样。

> Examples of strong and weak declarations:

strong和weak声明示例

```objectivec 
// GOOD:

@interface MyDelegate : NSObject

@property(nonatomic) NSString *doohickey;
@property(nonatomic, weak) NSString *parent;

@end


@implementation MyDelegate {
  IBOutlet NSButton *_okButton;  // Normal NSControl; implicitly weak on Mac only

  AnObjcObject *_doohickey;  // My doohickey
  __weak MyObjcParent *_parent;  // To send messages back (owns this instance)

  // non-NSObject pointers...
  CWackyCPPClass *_wacky;  // Strong, some cross-platform object
  CFDictionaryRef *_dict;  // Strong
}
@end
```

#### ARC （Automatic Reference Counting）

> Object ownership and lifetime are explicit when using ARC, so no additional
> comments are required for automatically retained objects.

当使用ARC时，对象所有权和生命周期很清晰，所以不需要额外的注释来说明自动引用计数变量。



## C语言特性（C Language Features）

### 宏（Macros）

> Avoid macros, especially where `const` variables, enums, XCode snippets, or C
> functions may be used instead.

若能使用`const`变量，枚举，Xcode代码片段，或C函数，请不要使用宏。

> Macros make the code you see different from the code the compiler sees. Modern C
> renders traditional uses of macros for constants and utility functions
> unnecessary. Macros should only be used when there is no other solution
> available.

宏会使你看到的代码和编译器看到的代码不同。现代C使用宏的的传统用途不再是常量和工具函数。现在宏只有在没有其他解决方案时才被使用。

> Where a macro is needed, use a unique name to avoid the risk of a symbol
> collision in the compilation unit. If practical, keep the scope limited by
> `#undefining` the macro after its use.

需要宏的地方，使用唯一的名字以避免在汇编时符号冲突。如果可行，使用`#undefining`限制宏的使用范围。

> Macro names should use `SHOUTY_SNAKE_CASE`—all uppercase letters with
> underscores between words. Function-like macros may use C function naming
> practices. Do not define macros that appear to be C or Objective-C keywords.

宏的名字应该使用`SHOUTY_SNAKE_CASE`形式——所有字母大写，使用下划线链接不同单词。函数类的宏使用函数的命名规范。不要定义和C或Objective-C关键字同名的宏。

```objectivec 
// GOOD:

#define GTM_EXPERIMENTAL_BUILD ...      // GOOD

// Assert unless X > Y
#define GTM_ASSERT_GT(X, Y) ...         // GOOD, macro style.

// Assert unless X > Y
#define GTMAssertGreaterThan(X, Y) ...  // GOOD, function style.
```

```objectivec 
// AVOID:

#define kIsExperimentalBuild ...        // AVOID

#define unless(X) if(!(X))              // AVOID
```

> Avoid macros that expand to unbalanced C or Objective-C constructs. Avoid macros
> that introduce scope, or may obscure the capturing of values in blocks.

*这一段突然不知道如何翻译*，大意是：避免使用会导致C或Objective-C构造方法错乱的宏，避免使用会引入作用域或让block中变量持有者模糊（防止内存泄漏）的宏。

> Avoid macros that generate class, property, or method definitions in
> headers to be used as public API. These only make the code hard to
> understand, and the language already has better ways of doing this.

避免在公用API头文件中使用可以生成类，属性或方法定义的宏。这种用法会导致代码难懂，而且语言本身有相对此方法更好的实现方法。

> Avoid macros that generate method implementations, or that generate declarations
> of variables that are later used outside of the macro. Macros shouldn't make
> code hard to understand by hiding where and how a variable is declared.

避免使用生成方法实现的宏（比如生成单例方法的宏等）或者可生成变量声明，且该变量在宏外使用的宏。宏不能隐藏变量在何处以及如何被声明，这会导致代码晦涩难懂。

```objectivec 
// AVOID:

#define ARRAY_ADDER(CLASS) \
  -(void)add ## CLASS ## :(CLASS *)obj toArray:(NSMutableArray *)array

ARRAY_ADDER(NSString) {
  if (array.count > 5) {              // AVOID -- where is 'array' defined?
    ...
  }
}
```

> Examples of acceptable macro use include assertion and debug logging macros
> that are conditionally compiled based on build settings—often, these are
> not compiled into release builds.

宏中使用assert或根据编译设置，进行debug有条件编译，这可以接受，一般情况下这些条件编译代码不会包含在release版本中。

### 非标准扩展宏（Nonstandard Extensions）

> Nonstandard extensions to C/Objective-C may not be used unless otherwise
> specified.

C/Objective-C非标准扩展宏，除非特别说明，否则不可使用。

> Compilers support various extensions that are not part of standard C. Examples
> include compound statement expressions (e.g. `foo = ({ int x; Bar(&x); x })`).

编译器支持大量的非标准C语言扩展宏。例如复合语句表达式(例如： `foo = ({ int x; Bar(&x); x })`).

> `__attribute__` is an approved exception, as it is used in Objective-C API
> specifications.

`__attribute__` 是一个在Objective-C API被认可和使用的扩展宏。

> The binary form of the conditional operator, `A ?: B`, is an approved exception.

对于三元运算符，`A ?: B`这种用法是个例外，也被认可使用。



## Cocoa&Objective-C特性 （Cocoa and Objective-C Features）

### 明确特定初始化器（Identify Designated Initializer）

> Clearly identify your designated initializer.

清晰指明你的特定初始化器（也可以理解成初始化方法）。

> It is important for those who might be subclassing your class that the
> designated initializer be clearly identified. That way, they only need to
> override a single initializer (of potentially several) to guarantee the
> initializer of their subclass is called. It also helps those debugging your
> class in the future understand the flow of initialization code if they need to
> step through it. Identify the designated initializer using comments or the
> `NS_DESIGNATED_INITIALIZER` macro. If you use `NS_DESIGNATED_INITIALIZER`, mark
> unsupported initializers with `NS_UNAVAILABLE`.

清晰的指明你创建的类的特定初始化器，这一点在其他人创建继承自你的类时显得非常重要。这样的话，他们只需要重写某一个或几个初始化器就可以保证他们的子类初始化方法被调用。这也可以帮助后面可能调试代码的人，更清晰的了解你的类初始化流程。请使用注释或者`NS_DESIGNATED_INITIALIZER` 宏指明你的特定初始化器。如果使用`NS_DESIGNATED_INITIALIZER` 宏，请将其他不支持的初始化器用 `NS_UNAVAILABLE`来标注。

### 重写指定初始化器（Override Designated Initializer）

> When writing a subclass that requires an `init...` method, make sure you
> override the designated initializer of the superclass.

若实现一个类需要 `init...` 方法，必须重写父类的指定初始化器。

> If you fail to override the designated initializer of the superclass, your
> initializer may not be called in all cases, leading to subtle and very difficult
> to find bugs.

如果不重写父类的指定初始化器，你自己的初始化器可能不会保证在所有情况下都被调用，这会导致bug很诡异，难以被发现。

### NSObject重写方法的放置位置（Overridden NSObject Method Placement)

> Put overridden methods of NSObject at the top of an `@implementation`.

将NSObject的重写方法置于`@implementation`部分的顶部。

> This commonly applies to (but is not limited to) the `init...`, `copyWithZone:`,
> and `dealloc` methods. The `init...` methods should be grouped together,
> followed by other typical `NSObject` methods such as `description`, `isEqual:`,
> and `hash`.

这通常用于但不局限于 `init...`, `copyWithZone:`, `dealloc`方法。 `init…` 一类的方法要集合放置在一起，后面可以放置其他 `NSObject` 常用方法，例如 `description`, `isEqual:`和 `hash`。

> Convenience class factory methods for creating instances may precede the
> `NSObject` methods.

便捷的创建对象的工厂方法可以放置在`NSObject` 之前。

### 初始化（Initialization）

> Don't initialize instance variables to `0` or `nil` in the `init` method; doing
> so is redundant.

不必在 `init` 方法中初始化实例变量为 `0` 或 `nil` ，多余！

> All instance variables for a newly allocated object are [initialized to](https://developer.apple.com/library/mac/documentation/General/Conceptual/CocoaEncyclopedia/ObjectAllocation/ObjectAllocation.html)
> `0` (except for isa), so don't clutter up the init method by re-initializing
> variables to `0` or `nil`.

所有新创建的实例变量都会被初始化为0（isa除外），所以不必散乱的在init初始化方法中将实例变量初始化为 `0` 或 `nil`。

### 头文件中的实例变量的作用域应该是@protected或@private（Instance Variables In Headers Should Be @protected or @private）

> Instance variables should typically be declared in implementation files or
> auto-synthesized by properties. When ivars are declared in a header file, they
> should be marked `@protected` or `@private`.

实例变量通常被放置在头文件中，或通过property被自动synthesize。若实例变量被声明在头文件中，这些成员变量需要被标记为 `@protected` 或 `@private`。

```objectivec 
// GOOD:

@interface MyClass : NSObject {
 @protected
  id _myInstanceVariable;
}
@end
```

### 不要使用+new（Do Not Use +new）

> Do not invoke the `NSObject` class method `new`, nor override it in a subclass.
> `+new` is rarely used and contrasts greatly with initializer usage. Instead, use
> `+alloc` and `-init` methods to instantiate retained objects.

不可调用NSObject的类方法`new`或在子类中重写该方法。`+new`方法很少使用，与初始化器的使用有很大的不同。相反，一般使用+alloc和-init方法来创建和初始化实例对象。

### 公开API保持简单（Keep the Public API Simple）

> Keep your class simple; avoid "kitchen-sink" APIs. If a method doesn't need to
> be public, keep it out of the public interface.

保持类简单，避免“kitchen-sink”（激进现实主义）API。如果一个方法不需要作为公开方法，请不要暴露在公开接口中。

> Unlike C++, Objective-C doesn't differentiate between public and private
> methods; any message may be sent to an object. As a result, avoid placing
> methods in the public API unless they are actually expected to be used by a
> consumer of the class. This helps reduce the likelihood they'll be called when
> you're not expecting it. This includes methods that are being overridden from
> the parent class.

和C++不同，Objective-C在公开方法和私有方法之间并没有什么太多区分，任何消息都可能被发送给对象。因此，只有使用者需要调用某一个方法时，才把这个方法放置在公开的API中。这样可以降低一些你不希望外界调用的方法被调用的可能性，这也包括重写的父类方法。

> Since internal methods are not really private, it's easy to accidentally
> override a superclass's "private" method, thus making a very difficult bug to
> squash. In general, private methods should have a fairly unique name that will
> prevent subclasses from unintentionally overriding them.

因为内部方法并不是真正的私有方法，也容易碰巧重写一个父类的私有方法，这样会导致很难排除由此引起的bug。通常隐私方法需要有一个较为独特的名字，这样可以防止子类无意的重写这些方法。

### #import和#include（#import and #include）

> `#import` Objective-C and Objective-C++ headers, and `#include` C/C++ headers.

使用`#import`引用Objective-C 和 Objective-C++头文件，用`#include` C/C++头文件。

> C/C++ headers include other C/C++ headers using `#include`. Using `#import`
> on C/C++ headers prevents future inclusions using `#include` and could result in
> unintended compilation behavior.
> C/C++ headers should provide their own `#define` guard.

C/C++头文件中引用其他C/C++头文件使用`#include`。使用`#import`引用C/C++头文件，以避免后面使用 `#include` 可能导致的头文件冲突和编译问题。

C/C++每个头文件中需要有自己`#define`保护，（以防止头文件被重复引用导致的重复编译的问题）。

### 头文件引用顺序（Order of Includes）

> The standard order for header inclusion is the related header, operating system
> headers, language library headers, and finally groups of headers for other
> dependencies.

标准头文件引用顺序为相关头文件、系统头文件、语言库头文件，最终是其他引用头文件。

> The related header precedes others to ensure it has no hidden dependencies.
> For implementation files the related header is the header file.
> For test files the related header is the header containing the tested interface.

相关头文件放在其他头文件前，可以保证其他隐藏依赖。对于implementation文件，它的相关头文件就是它自己的头文件。对于测试文件，它的相关头文件就是包含被测试接口的头文件。

> A blank line may separate logically distinct groups of included headers.

使用空行来区分不同类别的头文件。

> Within each group the includes should be ordered alphabetically.

不同类别的头文件，需要按字母顺序排列。

> Import headers using their path relative to the project's source directory.

以工程目录作为根目录，使用相对路径引用头文件。

```objectivec 
// GOOD:

#import "ProjectX/BazViewController.h"

#import <Foundation/Foundation.h>

#include <unistd.h>
#include <vector>

#include "base/basictypes.h"
#include "base/integral_types.h"
#include "util/math/mathutil.h"

#import "ProjectX/BazModel.h"
#import "Shared/Util/Foo.h"
```

### 使用系统库Umbrella头文件（Use Umbrella Headers for System Frameworks）

> Import umbrella headers for system frameworks and system libraries rather than
> include individual files.

引用系统库的umbrella头文件，而不是引用某几个单独的头文件。（关于umbrella头文件，更像是一个库中专门暴露出来，供外界使用者去引用的头文件，而不是引用库中的某些头文件，详细解析请Google）

> While it may seem tempting to include individual system headers from a framework
> such as Cocoa or Foundation, in fact it's less work on the compiler if you
> include the top-level root framework. The root framework is generally
> pre-compiled and can be loaded much more quickly. In addition, remember to use
> `@import` or `#import` rather than `#include` for Objective-C frameworks.

人们似乎更倾向引用Cocoa或Foundation系统库中单独的头文件，这样看起来引用更简单，但事实上，引用系统库的顶层头文件会让编译器做更少的工作。根框架通常会预处理，从而加载速度更快。另外，对于Objective-C框架，记住使用`@import`和`#import`，而不使用 `#include` 。

```objectivec 
// GOOD:

@import UIKit;     // GOOD.
#import <Foundation/Foundation.h>     // GOOD.
```

```objectivec 
// AVOID:

#import <Foundation/NSArray.h>        // AVOID.
#import <Foundation/NSString.h>
...
```

### 避免在初始化器或`-dealloc`中给当前对象发消息（Avoid Messaging the Current Object Within Initializers and `-dealloc`）

> Code in initializers and `-dealloc` should avoid invoking instance methods.

初始化器或 `-dealloc`方法中，避免调用该类对象的实例方法。

> Superclass initialization completes before subclass initialization. Until all
> classes have had a chance to initialize their instance state any method
> invocation on self may lead to a subclass operating on uninitialized instance
> state.

父类的初始化方法先于子类初始化方法执行。在所有类都被初始化，使该对象的所有属性被初始化之前调用该类的示例方法，都可能导致子类直接操作未初始化的属性。

> A similar issue exists for `-dealloc`, where a method invocation may cause a
> class to operate on state that has been deallocated.

 `-dealloc`方法中也存在类似问题，例如在`-dealloc`调用一些实例方法，这些方法操作的某些属性，可能早已被释放掉了。

> One case where this is less obvious is property accessors. These can be
> overridden just like any other selector. Whenever practical, directly assign to
> and release ivars in initializers and `-dealloc`, rather than rely on accessors.

属性访问是一种不太明显的案例。属性访问器可以像其他selector一样被重写。一旦切实可行，直接在初始化器和`-dealloc`方法中对成员变量进行赋值和释放，而不是通过属性访问器来完成。

```objectivec 
// GOOD:

- (instancetype)init {
  self = [super init];
  if (self) {
    _bar = 23;  // GOOD.
  }
  return self;
}
```

> Beware of factoring common initialization code into helper methods:
>
> - Methods can be overridden in subclasses, either deliberately, or
>   accidentally due to naming collisions.
> - When editing a helper method, it may not be obvious that the code is being
>   run from an initializer.

拆解通用初始化代码为工具方法要谨慎！

- 工具方法可能会有意或无意的被子类重写，或者碰巧产生了命名冲突；
- 当编辑一个工具方法时，可能不会知晓这段代码是被初始化方法调用的；

```objectivec 
// AVOID:

- (instancetype)init {
  self = [super init];
  if (self) {
    self.bar = 23;  // AVOID.
    [self sharedMethod];  // AVOID. Fragile to subclassing or future extension.
  }
  return self;
}
```

```objectivec 
// GOOD:

- (void)dealloc {
  [_notifier removeObserver:self];  // GOOD.
}
```

```objectivec 
// AVOID:

- (void)dealloc {
  [self removeNotifications];  // AVOID.
}
```

### Setter方法中NSStrings要Copy（Setters copy NSStrings）

> Setters taking an `NSString` should always copy the string it accepts. This is
> often also appropriate for collections like `NSArray` and `NSDictionary`.

Setter方法中对传入的`NSString`参数必须copy一份再使用，同样，对于容器类参数，例如 `NSArray`、 `NSDictionary`，也需要copy再使用。

> Never just retain the string, as it may be a `NSMutableString`. This avoids the
> caller changing it under you without your knowledge.

永远不要只考虑是string类型，也可能（传入的）是`NSMutableString`类型。这可以避免在你不知情的情况下，调用方修改该值。

> Code receiving and holding collection objects should also consider that the
> passed collection may be mutable, and thus the collection could be more safely
> held as a copy or mutable copy of the original.

持有容器对象参数也需要考虑该对象可能也是可变的，因此，使用该容器参数的复制对象，相对更安全。

```objectivec 
// GOOD:

@property(nonatomic, copy) NSString *name;

- (void)setZigfoos:(NSArray<Zigfoo *> *)zigfoos {
  // Ensure that we're holding an immutable collection.
  _zigfoos = [zigfoos copy];
}
```

### 用泛型标识元素类型（Use Lightweight Generics to Document Contained Types）

> All projects compiling on Xcode 7 or newer versions should make use of the
> Objective-C lightweight generics notation to type contained objects.

在Xcode7或更新版本编译的工程，应该使用Objective-C轻量级泛型符号来标识其包含的对象类别。

> Every `NSArray`, `NSDictionary`, or `NSSet` reference should be declared using
> lightweight generics for improved type safety and to explicitly document usage.

`NSArray`, `NSDictionary`, 或 `NSSet`对象都需要轻量级泛型符号标明，这可以改善类型安全以及明确文档使用说明。

```objectivec 
// GOOD:

@property(nonatomic, copy) NSArray<Location *> *locations;
@property(nonatomic, copy, readonly) NSSet<NSString *> *identifiers;

NSMutableArray<MyLocation *> *mutableLocations = [otherObject.locations mutableCopy];
```

> If the fully-annotated types become complex, consider using a typedef to
> preserve readability.

若要标识的泛型比较复杂，可以考虑使用typedef定义新类型，以保持可读性。

```objectivec 
// GOOD:

typedef NSSet<NSDictionary<NSString *, NSDate *> *> TimeZoneMappingSet;
TimeZoneMappingSet *timeZoneMappings = [TimeZoneMappingSet setWithObjects:...];
```

> Use the most descriptive common superclass or protocol available. In the most
> generic case when nothing else is known, declare the collection to be explicitly
> heterogenous using id.

使用最具描述性的常用父类或协议。通常情况下，当不知道容器中对象类型时，使用id显式声明。

```objectivec 
// GOOD:

@property(nonatomic, copy) NSArray<id> *unknowns;
```

### 避免抛异常（Avoid Throwing Exceptions）

> Don't `@throw` Objective-C exceptions, but you should be prepared to catch them
> from third-party or OS calls.

不要使用`@throw` 抛出Objective-C异常，但在使用第三库或系统调用时，你还必须要考虑如何捕获异常。

> This follows the recommendation to use error objects for error delivery in
> [Apple's Introduction to Exception Programming Topics for
> Cocoa](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/Exceptions/Exceptions.html).

这遵循关于错误对象错误传递的推荐说明文档：[Apple's Introduction to Exception Programming Topics for
Cocoa](https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/Exceptions/Exceptions.html).

> We do compile with `-fobjc-exceptions` (mainly so we get `@synchronized`), but
> we don't `@throw`. Use of `@try`, `@catch`, and `@finally` are allowed when
> required to properly use 3rd party code or libraries. If you do use them, please
> document exactly which methods you expect to throw.

我们编译时使用编译选项`-fobjc-exceptions`（通常也用`@synchronized`），但我们不使用`@throw`。当使用第三方库或代码时， `@try`, `@catch`和 `@finally` 是被允许使用的。如果确定使用了这些关键字，请清晰明确的指明哪些方法会抛出异常。

### `nil`检查 （`nil` Checks）

> Avoid `nil` pointer checks that exist only to prevent sending messages to `nil`.
> Sending a message to `nil` [reliably returns](http://www.sealiesoftware.com/blog/archive/2012/2/29/objc_explain_return_value_of_message_to_nil.html)
>
>  `nil` as a pointer, zero as an integer or floating-point value, structs initialized to `0`, and `_Complex` values equal to `{0, 0}`.

如果指针检查只是为了防止给nil对象发消息，那这部分检查不必添加。

给`nil`发消息的返回值是可靠的

返回值是指针时，返回nil；返回值是整数或浮点数时，返回0；返回值是结构体时，返回0；返回值是`_Complex`时，返回 `{0, 0}`。

*(上面这句我也没读懂，我也不打算不懂装懂)*

```objectivec 
// AVOID:

if (dataSource) {  // AVOID.
  [dataSource moveItemAtIndex:1 toIndex:0];
}
```

```objectivec 
// GOOD:

[dataSource moveItemAtIndex:1 toIndex:0];  // GOOD.
```

> Note that this applies to `nil` as a message target, not as a parameter value.
> Individual methods may or may not safely handle `nil` parameter values.

注意：这适用于 `nil` 作为消息接受者，而不是作为参数值。

个别方法可能会，也可能不会安全处理nil参数值。

> Note too that this is distinct from checking C/C++ pointers and block pointers
> against `NULL`, which the runtime does not handle and will cause your
> application to crash. You still need to make sure you do not dereference a
> `NULL` pointer.

也请注意这区别于检查C/C++指针和block指针是否为`NULL`, 这些运行时不会处理，这些会导致应用崩溃。你仍然需要检查指针不能为`NULL`。

### 可空性（Nullability）

> Interfaces can be decorated with nullability annotations to describe how the
> interface should be used and how it behaves. Use of nullability regions (e.g.,
> `NS_ASSUME_NONNULL_BEGIN` and `NS_ASSUME_NONNULL_END`) and explicit nullability
> annotations are both accepted. Prefer using the `_Nullable` and `_Nonnull`
> keywords over the `__nullable` and `__nonnull` keywords. For Objective-C methods
> and properties prefer using the context-sensitive, non-underscored keywords,
> e.g., `nonnull` and `nullable`.

Interface中可以使用可空性注解来描述接口行为和如何使用。使用可控性作用域（例如`NS_ASSUME_NONNULL_BEGIN` 和 `NS_ASSUME_NONNULL_END`）或使用可控性注解，这两种方式都是可以的。相对 `__nullable` 和 `__nonnull` 关键字，更推荐使用 `_Nullable`和 `_Nonnull`。对于Objective-C方法和属性，推荐使用无下划线的关键字，例如`nonnull` 和 `nullable`。

```objectivec 
// GOOD:

/** A class representing an owned book. */
@interface GTMBook : NSObject

/** The title of the book. */
@property(readonly, copy, nonnull) NSString *title;

/** The author of the book, if one exists. */
@property(readonly, copy, nullable) NSString *author;

/** The owner of the book. Setting nil resets to the default owner. */
@property(copy, null_resettable) NSString *owner;

/** Initializes a book with a title and an optional author. */
- (nonnull instancetype)initWithTitle:(nonnull NSString *)title
                               author:(nullable NSString *)author
    NS_DESIGNATED_INITIALIZER;

/** Returns nil because a book is expected to have a title. */
- (nullable instancetype)init;

@end

/** Loads books from the file specified by the given path. */
NSArray<GTMBook *> *_Nullable GTMLoadBooksFromFile(NSString *_Nonnull path);
```

```objectivec 
// AVOID:

NSArray<GTMBook *> *__nullable GTMLoadBooksFromTitle(NSString *__nonnull path);
```

> Be careful assuming that a pointer is not null based on a non-null qualifier
> because the compiler may not guarantee that the pointer is not null.

如果标识符标注某个指针不为空，也不要轻信，因为编译器可不能保证该指针不为空。

### BOOL陷阱（BOOL Pitfalls）

> Be careful when converting general integral values to `BOOL`. Avoid comparing
> directly with `YES`.

将整型数值转换为`BOOL`要小心。避免直接和 `YES`直接进行比较。

> `BOOL` in OS X and in 32-bit iOS builds is defined as a signed `char`, so it may
> have values other than `YES` (`1`) and `NO` (`0`). Do not cast or convert
> general integral values directly to `BOOL`.

在OSX和32位iOS系统版本中，`BOOL` 类型被定义为有符号`char`类型，所以，它可以是除了`YES` (`1`) and `NO` (`0`)之外的其他值。切勿将整数值直接赋值或强制类型转换后赋值给`BOOL`值。

> Common mistakes include casting or converting an array's size, a pointer value,
> or the result of a bitwise logic operation to a `BOOL` that could, depending on
> the value of the last byte of the integer value, still result in a `NO` value.
> When converting a general integral value to a `BOOL`, use ternary operators to
> return a `YES` or `NO` value.

常见错误包括将强转或转换数组大小、指针值或者通过逻辑位运算结果赋值给`BOOL`变量，根据整数最后一个字节的值，结果仍然有可能会产生`NO`值。在将一个整数转换为`BOOL`值时，需要使用三元运算符来保证返回值是`YES` 或 `NO`。

> You can safely interchange and convert `BOOL`, `_Bool` and `bool` (see C++ Std
> 4.7.4, 4.12 and C99 Std 6.3.1.2). Use `BOOL` in Objective-C method signatures.

Objective-C方法签名中使用`BOOL`，你可以安全的来转换 `BOOL`, `_Bool` and `bool`值（参考see C++ Std 4.7.4, 4.12 and C99 Std 6.3.1.2）。

> Using logical operators (`&&`, `||` and `!`) with `BOOL` is also valid and will
> return values that can be safely converted to `BOOL` without the need for a
> ternary operator.

也可以使用逻辑运算符(`&&`、 `||`、 `!`)来获取 `BOOL` 值，这种方法也可以不使用三元运算符来安全转换 `BOOL` 值。

```objectivec 
// AVOID:

- (BOOL)isBold {
  return [self fontTraits] & NSFontBoldTrait;  // AVOID.
}
- (BOOL)isValid {
  return [self stringValue];  // AVOID.
}
```

```objectivec 
// GOOD:

- (BOOL)isBold {
  return ([self fontTraits] & NSFontBoldTrait) ? YES : NO;
}
- (BOOL)isValid {
  return [self stringValue] != nil;
}
- (BOOL)isEnabled {
  return [self isValid] && [self isBold];
}
```

> Also, don't directly compare `BOOL` variables directly with `YES`. Not only is
> it harder to read for those well-versed in C, but the first point above
> demonstrates that return values may not always be what you expect.

同样，不要将 `BOOL` 值和`YES`进行直接比较。这样做不仅仅是因为对于精通C语言的人可能难以理解，而是返回值可能并不总是和预期一致（容易引起逻辑错误），这才是真正原因。

```objectivec 
// AVOID:

BOOL great = [foo isGreat];
if (great == YES) {  // AVOID.
  // ...be great!
}
```

```objectivec 
// GOOD:

BOOL great = [foo isGreat];
if (great) {         // GOOD.
  // ...be great!
}
```

### 无实例变量的Interface（Interfaces Without Instance Variables）

> Omit the empty set of braces on interfaces that do not declare any instance
> variables.

若interface不声明任何实例变量，省略空的大括号。

```objectivec 
// GOOD:

@interface MyClass : NSObject
// Does a lot of stuff.
- (void)fooBarBam;
@end
```

```objectivec 
// AVOID:

@interface MyClass : NSObject {
}
// Does a lot of stuff.
- (void)fooBarBam;
@end
```

## Cocoa模式（Cocoa Patterns）

### Delegate模式（Delegate Pattern）

> Delegates, target objects, and block pointers should not be retained when doing
> so would create a retain cycle.

Delegate，target对象，block指针不可使用retain，不然会产生循环引用。

> To avoid causing a retain cycle, a delegate or target pointer should be released
> as soon as it is clear there will no longer be a need to message the object.

为避免引起循环引用，delegate或响应对象指针需要被及时清理，以便后续发送的消息不再被响应。

> If there is no clear time at which the delegate or target pointer is no longer
> needed, the pointer should only be retained weakly.

若delegate或响应对象指针在后续不被需要时，没有一个清晰的时间点，那么该delegate或响应对象指针应该被设置为弱引用。

> Block pointers cannot be retained weakly. To avoid causing retain cycles in the
> client code, block pointers should be used for callbacks only where they can be
> explicitly released after they have been called or once they are no longer
> needed. Otherwise, callbacks should be done via weak delegate or target
> pointers.

Block指针不可使用弱引用。为避免在客户端代码中出现循环引用，block指针只有在被调用一次或者他们不被需要时会被明确的清理，才可以用于回调方法。否则，回调方法应该通过弱引用的delegate或者响应对象指针来实现。



## Objective-C++ 

### 代码风格与所用语言保持一致（Style Matches the Language）

> Within an Objective-C++ source file, follow the style for the language of the
> function or method you're implementing. In order to minimize clashes between the
> differing naming styles when mixing Cocoa/Objective-C and C++, follow the style
> of the method being implemented.

对于Objective-C++源码文件，遵守函数或方法实现语言的编码规范。为了将Cocoa/Objective-C、C++不同语言混合使用导致的命名风格冲突最小化，遵守源码中方法实现使用的编码风格。

> For code in an `@implementation` block, use the Objective-C naming rules. For
> code in a method of a C++ class, use the C++ naming rules.

对于 `@implementation`代码，使用Objective-C命名规范。对于C++类中方法代码，使用C++命名规范。

> For code in an Objective-C++ file outside of a class implementation, be
> consistent within the file.

对于Objective-C++文件类实现部分之外的代码，与该文件代码风格保持一致。

```objectivec++ 
// GOOD:

// file: cross_platform_header.h

class CrossPlatformAPI {
 public:
  ...
  int DoSomethingPlatformSpecific();  // impl on each platform
 private:
  int an_instance_var_;
};

// file: mac_implementation.mm
#include "cross_platform_header.h"

/** A typical Objective-C class, using Objective-C naming. */
@interface MyDelegate : NSObject {
 @private
  int _instanceVar;
  CrossPlatformAPI* _backEndObject;
}

- (void)respondToSomething:(id)something;

@end

@implementation MyDelegate

- (void)respondToSomething:(id)something {
  // bridge from Cocoa through our C++ backend
  _instanceVar = _backEndObject->DoSomethingPlatformSpecific();
  NSString* tempString = [NSString stringWithFormat:@"%d", _instanceVar];
  NSLog(@"%@", tempString);
}

@end

/** The platform-specific implementation of the C++ class, using C++ naming. */
int CrossPlatformAPI::DoSomethingPlatformSpecific() {
  NSString* temp_string = [NSString stringWithFormat:@"%d", an_instance_var_];
  NSLog(@"%@", temp_string);
  return [temp_string intValue];
}
```

> Projects may opt to use an 80 column line length limit for consistency with
> Google's C++ style guide.

工程中可能选择使用80个字符列宽限制，以便和Google的C++代码规范保持一致。



## 空间布局和格式（Spacing and Formatting） 

### 空格 vs 制表符（Spaces vs. Tabs） 

> Use only spaces, and indent 2 spaces at a time. We use spaces for indentation.
> Do not use tabs in your code.

只使用空格，缩进量为2个空格宽度。缩进时不使用制表符，只用空格。

> You should set your editor to emit spaces when you hit the tab key, and to trim
> trailing spaces on lines.

设置编辑器使用空格自动替换制表符，并消除行位空格。

### 行宽（Line Length） 

> The maximum line length for Objective-C files is 100 columns.

> You can make violations easier to spot by enabling *Preferences > Text Editing >
> Page guide at column: 100* in Xcode.

Objective-C最大行宽为100列（100字符宽度）。在xCode中，通过设置Preferences > Text Editing > Page guide at column:为100，可以轻松检查超宽地方。

### 方法声明与定义（Method Declarations and Definitions） 

> One space should be used between the `-` or `+` and the return type, and no
> spacing in the parameter list except between parameters.

`-` or `+` 后与返回值之间须有一个空格，参数名与参数类型间无空格，参数列表不同参数间有一个空格；

> Methods should look like this:

方法示例如下：

```objectivec 
// GOOD:

- (void)doSomethingWithString:(NSString *)theString {
  ...
}
```

> The spacing before the asterisk is optional. When adding new code, be consistent
> with the surrounding file's style.

星号前可以有一个空格。新添加的代码要与文件代码风格保持一致。

> If a method declaration does not fit on a single line, put each parameter on its
> own line. All lines except the first should be indented at least four spaces.
> Colons before parameters should be aligned on all lines. If the colon before the
> parameter on the first line of a method declaration is positioned such that
> colon alignment would cause indentation on a subsequent line to be less than
> four spaces, then colon alignment is only required for all lines except the
> first.

如果一个方法声明一行放不下，需要将不同参数各占一行。除首行外，其余所有行都要至少缩进4个空格。不同参数前的冒号要对齐。如果方法声明第一行中参数前的冒号所在位置，对齐所有冒号后，后面的参数前面缩进的空格数少于4个，这种情况只需要将函数声明中第一行之外的其他行冒号对齐即可。

```objectivec 
// GOOD:

- (void)doSomethingWithFoo:(GTMFoo *)theFoo
                      rect:(NSRect)theRect
                  interval:(float)theInterval {
  ...
}

- (void)shortKeyword:(GTMFoo *)theFoo
            longerKeyword:(NSRect)theRect
    someEvenLongerKeyword:(float)theInterval
                    error:(NSError **)theError {
  ...
}

- (id<UIAdaptivePresentationControllerDelegate>)
    adaptivePresentationControllerDelegateForViewController:(UIViewController *)viewController;

- (void)presentWithAdaptivePresentationControllerDelegate:
    (id<UIAdaptivePresentationControllerDelegate>)delegate;
```



### 方法声明与定义（Function Declarations and Definitions）

> Prefer putting the return type on the same line as the function name and append
> all parameters on the same line if they will fit. Wrap parameter lists which do
> not fit on a single line as you would wrap arguments in a [function
> call](#Function_Calls).

将方法返回类型和方法名放于同一行，后面跟其他参数，如果一行能放下，则参数放于同一行。若一行放不下，就像函数调用一样，来包装参数列表。

```objectivec 
// GOOD:

NSString *GTMVersionString(int majorVersion, minorVersion) {
  ...
}

void GTMSerializeDictionaryToFileOnDispatchQueue(
    NSDictionary<NSString *, NSString *> *dictionary,
    NSString *filename,
    dispatch_queue_t queue) {
  ...
}
```

> Function declarations and definitions should also satisfy the following
> conditions:
>
> - The opening parenthesis must always be on the same line as the function
>   name.
> - If you cannot fit the return type and the function name on a single line,
>   break between them and do not indent the function name.
> - There should never be a space before the opening parenthesis.
> - There should never be a space between function parentheses and parameters.
> - The open curly brace is always on the end of the last line of the function
>   declaration, not the start of the next line.
> - The close curly brace is either on the last line by itself or on the same
>   line as the open curly brace.
> - There should be a space between the close parenthesis and the open curly
>   brace.
> - All parameters should be aligned if possible.
> - Function scopes should be indented 2 spaces.
> - Wrapped parameters should have a 4 space indent.

函数声明和定义也需要满足以下条件：

- 函数名后的左括号必须和函数名在同一行；
- 若返回值类型和函数名不能放在同一行，在他们之间换行，并且不缩进函数名；
- 函数名后的左括号前无空格；
- 函数括号和参数间无空格；
- 函数左大括号在函数声明后，不可另起一行；
- 函数右大括号在函数最后独占一行，或和左大括号同一行；
- 函数左大括号和函数参数右括号间，有一个空格；
- 所有参数尽量对齐（冒号对齐）；
- 函数作用域缩进2个空格；
- 封装参数缩进4个空格；



### 条件判断（Conditionals） 

> Include a space after `if`, `while`, `for`, and `switch`, and around comparison
> operators.

 `if`, `while`, `for`,  `switch`后有一个空格，比较运算符两边有空格。

```objectivec 
// GOOD:

for (int i = 0; i < 5; ++i) {
}

while (test) {};
```

> Braces may be omitted when a loop body or conditional statement fits on a single
> line.

若循环体或条件语句可放置一行中时，可以省略大括号；

```objectivec 
// GOOD:

if (hasSillyName) LaughOutLoud();

for (int i = 0; i < 10; i++) {
  BlowTheHorn();
}
```

```objectivec 
// AVOID:

if (hasSillyName)
  LaughOutLoud();               // AVOID.

for (int i = 0; i < 10; i++)
  BlowTheHorn();                // AVOID.
```

> If an `if` clause has an `else` clause, both clauses should use braces.

若 `if` 语句后有 `else` 语句，两部分都需要使用大括号。

```objectivec 
// GOOD:

if (hasBaz) {
  foo();
} else {  // The else goes on the same line as the closing brace.
  bar();
}
```

```objectivec 
// AVOID:

if (hasBaz) foo();
else bar();        // AVOID.

if (hasBaz) {
  foo();
} else bar();      // AVOID.
```

> Intentional fall-through to the next case should be documented with a comment
> unless the case has no intervening code before the next case.

除非两个case语句之间没有其他代码，有意添加的case连续执行情况，需要增加注释说明。

```objectivec 
// GOOD:

switch (i) {
  case 1:
    ...
    break;
  case 2:
    j++;
    // Falls through.
  case 3: {
    int k;
    ...
    break;
  }
  case 4:
  case 5:
  case 6: break;
}
```

### 表达式（Expressions）

> Use a space around binary operators and assignments. Omit a space for a unary
> operator. Do not add spaces inside parentheses.

二进制运算符、赋值运算符左右两边都需要添加空格。一元运算符可以省略空格。圆括号（左括号右边、右括号左边）不用空格。

```objectivec 
// GOOD:

x = 0;
v = w * x + y / z;
v = -y * (x + z);
```

> Factors in an expression may omit spaces.

某些表达式运算符左右可能省略空格。

```objectivec 
// GOOD:

v = w*x + y/z;
```

### 方法调动（Method Invocations）

> Method invocations should be formatted much like method declarations.

方法调用的格式应与方法声明一致。

> When there's a choice of formatting styles, follow the convention already used
> in a given source file. Invocations should have all arguments on one line:

若源码中有现有的编码规范使用惯例，请保持一致继续使用。方法调用的所有参数都放在一行。

```objectivec 
// GOOD:

[myObject doFooWith:arg1 name:arg2 error:arg3];
```

> or have one argument per line, with colons aligned:

或每个参数放在单独一行，冒号对齐。

```objectivec 
// GOOD:

[myObject doFooWith:arg1
               name:arg2
              error:arg3];
```

> Don't use any of these styles:

不要使用下列编码风格：

```objectivec 
// AVOID:

[myObject doFooWith:arg1 name:arg2  // some lines with >1 arg
              error:arg3];

[myObject doFooWith:arg1
               name:arg2 error:arg3];

[myObject doFooWith:arg1
          name:arg2  // aligning keywords instead of colons
          error:arg3];
```

> As with declarations and definitions, when the first keyword is shorter than the
> others, indent the later lines by at least four spaces, maintaining colon
> alignment:

与声明和定义一样，当第一个关键字比其他字段短，将后面的参数缩进至少4个空格，并将冒号对齐。

```objectivec 
// GOOD:

[myObj short:arg1
          longKeyword:arg2
    evenLongerKeyword:arg3
                error:arg4];
```

> Invocations containing multiple inlined blocks may have their parameter names
> left-aligned at a four space indent.

方法调用包含多个内嵌block时，将这些参数缩进4个空格，并左对齐。



### 函数调用（Function Calls）

> Function calls should include as many parameters as fit on each line, except
> where shorter lines are needed for clarity or documentation of the parameters.

函数调用要尽可能多的将参数填满每一行，如果某些参数需要说明参数含义或添加文档说明，将这行参数不填满整行。

> Continuation lines for function parameters may be indented to align with the
> opening parenthesis, or may have a four-space indent.

换行后的参数需要与函数的左括号对齐，或者使用4个空格进行缩进。

```objectivec 
// GOOD:

CFArrayRef array = CFArrayCreate(kCFAllocatorDefault, objects, numberOfObjects,
                                 &kCFTypeArrayCallBacks);

NSString *string = NSLocalizedStringWithDefaultValue(@"FEET", @"DistanceTable",
    resourceBundle,  @"%@ feet", @"Distance for multiple feet");

UpdateTally(scores[x] * y + bases[x],  // Score heuristic.
            x, y, z);

TransformImage(image,
               x1, x2, x3,
               y1, y2, y3,
               z1, z2, z3);
```

> Use local variables with descriptive names to shorten function calls and reduce
> nesting of calls.

使用具有描述性名称的局部变量来缩短函数调用和减少内嵌调用。

```objectivec 
// GOOD:

double scoreHeuristic = scores[x] * y + bases[x];
UpdateTally(scoreHeuristic, x, y, z);

// AVOID
UpdateTally((scores[x] * y + bases[x]), x, y, z);
```



### 异常（Exceptions）

> Format exceptions with `@catch` and `@finally` labels on the same line as the
> preceding `}`. Add a space between the `@` label and the opening brace (`{`), as
> well as between the `@catch` and the caught object declaration. If you must use
> Objective-C exceptions, format them as follows. However, see [Avoid Throwing
> Exceptions](#Avoid_Throwing_Exceptions) for reasons why you should not be using
> exceptions.

使用 `@catch` 和 `@finally` 标签要与左大括号在同一行。标签与左大括号之间添加一个空格， `@catch` 与异常对象声明之间也添加一个空格。如果必须使用Objective-C异常类型，请按下面方式进行格式化。但是，请参考[避免抛异常（Avoid Throwing Exceptions）](#避免抛异常（Avoid Throwing Exceptions）) 以便了解避免抛出异常的原因。

```objectivec 
// GOOD:

@try {
  foo();
} @catch (NSException *ex) {
  bar(ex);
} @finally {
  baz();
}
```



### 函数长度（Function Length）

> Prefer small and focused functions.

推荐小而功能专注的函数。

> Long functions and methods are occasionally appropriate, so no hard limit is
> placed on function length. If a function exceeds about 40 lines, think about
> whether it can be broken up without harming the structure of the program.

长方法或者函数某些情况下也是可以的，所以关于函数长度没有固定的限制。如果一个函数长度超过了40个字符，请考虑如何在不破坏代码结构的基础上，将它拆分。

> Even if your long function works perfectly now, someone modifying it in a few
> months may add new behavior. This could result in bugs that are hard to find.
> Keeping your functions short and simple makes it easier for other people to read
> and modify your code.

即便你现在的长方法可以完美运行，可能几个月后的某些修改会给他添加新特性。这也导致出现问题难以发现。保持函数简练可以使代码易读，利于修改。

> When updating legacy code, consider also breaking long functions into smaller
> and more manageable pieces.

当更新遗留代码时，也需要考虑将长函数分解成更小更利于管理维护的部分。



### 垂直空白（Vertical Whitespace）

> Use vertical whitespace sparingly.

谨慎使用垂直空白。

> To allow more code to be easily viewed on a screen, avoid putting blank lines
> just inside the braces of functions.

为了让更多代码能够一屏展示，在函数大括号内，避免使用空行。

> Limit blank lines to one or two between functions and between logical groups of
> code.

不同函数间或不同代码逻辑组之间，空行限制在1-2行。



## Objective-C风格异常（Objective-C Style Exceptions）

### 指明风格异常（Indicating style exceptions）

> Lines of code that are not expected to adhere to these style recommendations
> require `// NOLINT` at the end of the line or `// NOLINTNEXTLINE` at the end of
> the previous line. Sometimes it is required that parts of Objective-C code must
> ignore these style recommendations (for example code may be machine generated or
> code constructs are such that its not possible to style correctly).

预计不符合这些规范的代码行，需要在行尾添加`// NOLINT`或者在前一行添加 `// NOLINTNEXTLINE` 标识。有时一部分代码需要忽略某些推荐的编码风格规范（例如某些机器生成的代码或者某些结构是不可能设置为正式样式的代码）。

> A `// NOLINT` comment on that line or `// NOLINTNEXTLINE` on the previous line
> can be used to indicate to the reader that code is intentionally ignoring style
> guidelines. In addition these annotations can also be picked up by automated
> tools such as linters and handle code correctly. Note that there is a single
> space between `//` and `NOLINT*`.

一行中的 `// NOLINT` 标注和前一行的 `// NOLINTNEXTLINE` 标注可以被用来告诉读者，某些代码是故意忽略遵守使用编码规范的，此外，这些标注也可以让一些自动化工具（如linters）正确处理代码。

注意 `//` 和 `NOLINT*`之间有一个空格。