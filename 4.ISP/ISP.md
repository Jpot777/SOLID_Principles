# ISP (Interface Segregation Principle)

• 정의 : 하나의 일반적인 interface 보다는 여러개의 구체적인 interface가 좋다라는 원칙!
장점은 시스템 내부 의존성을 느슨하게 하여 리팩토링, 수정, 재배포를 쉽게 할 수 있도록 한다!

```cs
// 이동 기능을 가진 인터페이스
public interface IMovable
{
    void Move(Vector3 direction);
}

// 점프 기능을 가진 인터페이스
public interface IJumpable
{
    void Jump(float height);
}

// 플레이어 클래스는 '이동 기능'과 '점프 기능'을 모두 가짐
public class Player : IMovable, IJumpable
{
    public void Move(Vector3 direction)
    {
        // 이동 로직 구현
    }

    public void Jump(float height)
    {
        // 점프 로직 구현
    }
}

// 몬스터 클래스는 이동 기능만 가짐
public class Monster : IMovable
{
    public void Move(Vector3 direction)
    {
        // 이동 로직 구현
    }
}
```

위 코드에서 <span style="color:brown">'IMovable'</span> 인터페이스와 <span style="color:brown">'IJumpable'</span> 인터페이스를 선언한다! <span style="color:blue">'Player' 클래스</span>는 <span style="color:brown">'IMovable' 인터페이스</span>와 <span style="color:brown">'IJumpable' 인터페이스</span>를 모두 구현하여 '이동 기능', '점프 기능'을 모두 가진다! 반면, <span style="color:red">'Monster' 클래스</span>는 <span style="color:brown">'IMovable' 인터페이스</span>만 구현하여 이동 기능만 가진다. 결론적으로 인터페이스를 분리시킴으로서 인터페이스 간의 의존성이 최소화 된다! 또한 인터페이스의 변경으로 인한 영향도를 최소화할 수 있다.
