# 模板

作者：谢辛 / Xin Xie / CheaSim
原文：https://www.cheasim.com/2018/09/30/%E6%A8%A1%E6%9D%BF/
发布日期：2018-09-30
更新日期：2018-09-30





# Java大数模板

二、Java之输入输出处理由于ACM竞赛题目的输入数据和输出数据一般有多组（不定），并且格式多种多样，所以，如何处理题目的输入输出是对大家的一项最基本的要求。这也是困扰初学者的一大问题。

- 输入：

格式1：Scanner sc = new Scanner (new BufferedInputStream(System.in));

格式2：Scanner sc = new Scanner (System.in);

在读入数据量大的情况下，格式1的速度会快些。

读一个整数： int n = sc.nextInt(); 相当于 scanf(“%d”, &n); 或 cin >> n;

读一个字符串：String s = sc.next(); 相当于 scanf(“%s”, s); 或 cin >> s;

读一个浮点数：double t = sc.nextDouble(); 相当于 scanf(“%lf”, &t); 或 cin >> t;

读一整行： String s = sc.nextLine(); 相当于 gets(s); 或 cin.getline(…);

判断是否有下一个输入可以用sc.hasNext()或sc.hasNextInt()或sc.hasNextDouble()或sc.hasNextLine()

```java
import
import
Scanner cin = new
while
//操作
}
```

### 大数使用例子

```java
import
import
import

public
static
public
int
BigInteger b = in.nextBigInteger();
BigDecimal c = in.nextBigDecimal();
/*
BigDecimal：
构造方法:
BigDecimal(BigInteger val)
BigDecimal(BigInteger unscaledVal, int scale)
BigDecimal(BigInteger unscaledVal, int scale, MathContext mc)
BigDecimal(BigInteger val, MathContext mc)
BigDecimal(char[] in)
BigDecimal(char[] in, int offset, int len)
BigDecimal(char[] in, int offset, int len, MathContext mc)
BigDecimal(char[] in, MathContext mc)
BigDecimal(double val)
BigDecimal(double val, MathContext mc)
BigDecimal(int val)
BigDecimal(int val, MathContext mc)
BigDecimal(long val)
BigDecimal(long val, MathContext mc)
BigDecimal(String val)
BigDecimal(String val, MathContext mc)
成员方法:
BigDecimal 	abs()
BigDecimal 	abs(MathContext mc)
BigDecimal 	add(BigDecimal augend)
BigDecimal 	add(BigDecimal augend, MathContext mc)
byte 	byteValueExact()
int 	compareTo(BigDecimal val)
BigDecimal 	divide(BigDecimal divisor)
BigDecimal 	divide(BigDecimal divisor, int roundingMode)
BigDecimal 	divide(BigDecimal divisor, int scale, int roundingMode)
BigDecimal 	divide(BigDecimal divisor, int scale, RoundingMode roundingMode)
BigDecimal 	divide(BigDecimal divisor, MathContext mc)
BigDecimal 	divide(BigDecimal divisor, RoundingMode roundingMode)
BigDecimal[] 	divideAndRemainder(BigDecimal divisor)
BigDecimal[] 	divideAndRemainder(BigDecimal divisor, MathContext mc)
BigDecimal 	divideToIntegralValue(BigDecimal divisor)
BigDecimal 	divideToIntegralValue(BigDecimal divisor, MathContext mc)
double 	doubleValue()
boolean 	equals(Object x)
float 	floatValue()
int 	hashCode()
int 	intValue()
int 	intValueExact()
long 	longValue()
long 	longValueExact()
BigDecimal 	max(BigDecimal val)
BigDecimal 	min(BigDecimal val)
BigDecimal 	movePointLeft(int n)
BigDecimal 	movePointRight(int n)
BigDecimal 	multiply(BigDecimal multiplicand)
BigDecimal 	multiply(BigDecimal multiplicand, MathContext mc)
BigDecimal 	negate()
BigDecimal 	negate(MathContext mc)
BigDecimal 	plus()
BigDecimal 	plus(MathContext mc)
BigDecimal 	pow(int n)
BigDecimal 	pow(int n, MathContext mc)
int 	precision()
BigDecimal 	remainder(BigDecimal divisor)
BigDecimal 	remainder(BigDecimal divisor, MathContext mc)
BigDecimal 	round(MathContext mc)
int 	scale()
BigDecimal 	scaleByPowerOfTen(int n)
BigDecimal 	setScale(int newScale)
Returns a BigDecimal whose scale is the specified value, and whose value is numerically equal to this BigDecimal's.
BigDecimal 	setScale(int newScale, int roundingMode)
BigDecimal 	setScale(int newScale, RoundingMode roundingMode)
Returns a BigDecimal whose scale is the specified value, and whose unscaled value is determined by multiplying or dividing this BigDecimal's unscaled value by the appropriate power of ten to maintain its overall value.
short 	shortValueExact()
int 	signum()
Returns the signum function of this BigDecimal. (1,0,-1)
BigDecimal 	stripTrailingZeros()
Returns a BigDecimal which is numerically equal to this one but with any trailing zeros removed from the representation.
BigDecimal 	subtract(BigDecimal subtrahend)
BigDecimal 	subtract(BigDecimal subtrahend, MathContext mc)
BigInteger 	toBigInteger()
BigInteger 	toBigIntegerExact()
String 	toEngineeringString()
String 	toPlainString()
String 	toString()
BigDecimal 	ulp()
Returns the size of an ulp, a unit in the last place, of this BigDecimal.
BigInteger 	unscaledValue()
static BigDecimal 	valueOf(double val)
static BigDecimal 	valueOf(long val)
static BigDecimal 	valueOf(long unscaledVal, int scale)
*/
BigDecimal test = new
test = test.setScale(3
System.out.println(test);
test = test.setScale(7
System.out.println(test);
test = test.divide(new
System.out.println(test);

/*
BigInteger:
构造方法:
BigInteger(byte[] val)
BigInteger(int signum, byte[] magnitude)
BigInteger(int bitLength, int certainty, Random rnd)
Constructs a randomly generated positive BigInteger that is probably prime, with the specified bitLength.
BigInteger(int numBits, Random rnd)
Constructs a randomly generated BigInteger, uniformly distributed over the range 0 to (2numBits - 1), inclusive.
BigInteger(String val)
BigInteger(String val, int radix)
成员方法:
BigInteger 	abs()
BigInteger 	add(BigInteger val)
BigInteger 	and(BigInteger val)
BigInteger 	andNot(BigInteger val)
Returns a BigInteger whose value is (this & ~val).
int 	bitCount()
Returns the number of bits in the two's complement representation of this BigInteger that differ from its sign bit.
int 	bitLength()
Returns the number of bits in the minimal two's-complement representation of this BigInteger, excluding a sign bit.
BigInteger 	clearBit(int n)
Returns a BigInteger whose value is equivalent to this BigInteger with the designated bit cleared.
int 	compareTo(BigInteger val)
BigInteger 	divide(BigInteger val)
BigInteger[] 	divideAndRemainder(BigInteger val)
double 	doubleValue()
boolean 	equals(Object x)
BigInteger 	flipBit(int n)
Returns a BigInteger whose value is equivalent to this BigInteger with the designated bit flipped.
float 	floatValue()
BigInteger 	gcd(BigInteger val)
Returns a BigInteger whose value is the greatest common divisor of abs(this) and abs(val).
int 	getLowestSetBit()
Returns the index of the rightmost (lowest-order) one bit in this BigInteger (the number of zero bits to the right of the rightmost one bit).
int 	hashCode()
int 	intValue()
boolean 	isProbablePrime(int certainty)
Returns true if this BigInteger is probably prime, false if it's definitely composite.
long 	longValue()
BigInteger 	max(BigInteger val)
BigInteger 	min(BigInteger val)
BigInteger 	mod(BigInteger m)
BigInteger 	modInverse(BigInteger m)
Returns a BigInteger whose value is (this^-1 mod m).
BigInteger 	modPow(BigInteger exponent, BigInteger m)
BigInteger 	multiply(BigInteger val)
BigInteger 	negate()
BigInteger 	nextProbablePrime()
Returns the first integer greater than this BigInteger that is probably prime.
BigInteger 	not()
BigInteger 	or(BigInteger val)
BigInteger 	pow(int exponent)
static BigInteger 	probablePrime(int bitLength, Random rnd)
Returns a positive BigInteger that is probably prime, with the specified bitLength.
BigInteger 	remainder(BigInteger val)
Returns a BigInteger whose value is (this % val).
BigInteger 	setBit(int n)
Returns a BigInteger whose value is equivalent to this BigInteger with the designated bit set.
BigInteger 	shiftLeft(int n)
Returns a BigInteger whose value is (this > n).
int 	signum()
BigInteger 	subtract(BigInteger val)
boolean 	testBit(int n)
Returns true if and only if the designated bit is set.
byte[] 	toByteArray()
String 	toString()
String 	toString(int radix)
static BigInteger 	valueOf(long val)
BigInteger 	xor(BigInteger val)
*/

MyPair[] pairs = new
Arrays.sort(pairs);
Arrays.binarySearch(pairs, 1
/*
二分查找
如果元素在数组中，则值为0~n-1，否则值为-1~-(n+1)，表示第一个比它大的值的位置，下标从1开始
*/
List pairList = new
pairList.add(new
//pairList.sort();
pairList.sort(new
Collections.shuffle(pairList);
Collections.swap(pairList, 1
Collections.sort(pairList);
}
}

class
int

@Override
public
MyPair b = (MyPair)o;
if
else
return
}
}

class
@Override
public
if
else
return
}
}
```

# 关于树的

## 树链剖分

```cpp
#include
using
#define
#define
#define
#define
#define
#define
void
int
a = b;
b = temp;
}
typedef
typedef
const
//head
const
int
int
int
struct
int
}G[maxn
模板

https://www.cheasim.com/%E6%A8%A1%E6%9D%BF/2018/09/30/%E6%A8%A1%E6%9D%BF.html

作者
CheaSim

发布于
2018-09-30

更新于
2019-05-11

许可协议

#[模板](https://www.cheasim.com/tags/%E6%A8%A1%E6%9D%BF/)




