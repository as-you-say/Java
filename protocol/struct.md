# Struct

C/C++ 언어로 개발되어있는 프로그램과 Java 언어로 되어있는 프로그램과 서로 통신할 수 있는 인터페이스를 제공해줍니다.  


## 1. 프로토콜 객체

### 1.1 구조체의 데이터 타입

C 서버와 Java 서버 사이에서 통신을 위한 데이터 타입입니다.  
아래 테이블을 참조해서 Struct 클래스를 상속받은 자바 클래스를 생성해서 사용합니다.

| No | C | Java |
| :---: | :---: | :---: |
| 1 | UCHAR | Unsigned8 |
| 2 | UWORD | Unsigned16 |
| 3 | UINT | Unsigned32 |
| 4 | byte | Signed8 |
| 5 | short | Signed16 |
| 6 | int | Signed32 |
| 7 | long | Signed64 |
| 8 | long long | Signed64 |
| 9 | float | Float32 |
| 10 | double | Float64 |
| 11 | pointer | Reference32 |
| 12 | char\[ \] | UTF8String |
| 13 | enum | Enum32 |

### 1.2 바이트 순서 - 엔디안

앤디언은 컴퓨터의 메모리와 같은 1차원의 공간에 여러 개의 연속된 대상을 배열하는 방법입니다.

앤디언은 보통 큰 단위가 앞에 나오는 빅 앤디언 작은 단위가 앞에 나오는 리틀 앤디언 둘을 모두 지원하는 미들 앤디언으로 구분합니다.

빅 앤디언은 최상위바이트\(MSB - Most Significant Byte\)부터 차례로 저장하는 방식이며, 리틀 앤디언은 최하위바이트\(LSB - Least Significant Byte\)부터 차례로 저장하는 방식입니다.









### 1.3 압축 여부







###  1.4 샘플코드

```java
import java.nio.ByteOrder;
import javolution.io.Struct;

public class Date extends Struct{

	// 구조체
	public final Unsigned16 year = new Unsigned16();
  public final Unsigned8 month = new Unsigned8();
  public final Unsigned8 day = new Unsigned8();

	// 바이트 순서 (최상위->최하위 / 최하위->최상위)
	@Override
	public ByteOrder byteOrder() {
		return ByteOrder.nativeOrder();
	}
	
	// 압축여부
	@Override
	public boolean isPacked() {
		return true;
	}
	
}
```









