# Struct

C씨 언어 CdfCccafdfas12312

## 1. Header

```java
import java.nio.ByteOrder;
import javolution.io.Struct;

public class DataHeader extends Struct{
	
	public final UTF8String idCode = new UTF8String(16);
	public final Signed32 totalRecords = new Signed32();
	public final DayIndex[] dayIndex = array(new DayIndex[32]);

	@Override
	public ByteOrder byteOrder() {
		return ByteOrder.LITTLE_ENDIAN;
	}
	
	@Override
	public boolean isPacked() {
		return true;
	}
	
}
```

