# DIP (Dependency Inversion Principle)

• 정의 : 상위 모듈은 하위 모듈에 종속되어서는 안된다. 둘 다 추상화에 의존해야 한다는 원칙!
의존 관계를 맺을 때, 변화하기 쉬운것(class) 보다는 변화하기 어려운것(interface, abstract)에 의존해야 한다는 원칙!

```cs
// 이동 기능을 가진 인터페이스
public interface IMovable
{
    void Move(Vector3 direction);
}

// 이동을 제어하는 클래스
public class MoveController
{
    private IMovable movable;

    public MoveController(IMovable movable)
    {
        this.movable = movable;
    }

    public void Move(Vector3 direction)
    {
        movable.Move(direction);
    }
}

// 플레이어 클래스는 이동 기능을 구현한 IMovable 인터페이스를 구현
public class Player : MonoBehaviour, IMovable
{
    public void Move(Vector3 direction)
    {
        // 이동 로직 구현
    }

    private MoveController moveController;

    private void Awake()
    {
        // MoveController를 생성할 때 인터페이스를 파라미터로 넘겨줌
        moveController = new MoveController(this);
    }

    private void Update()
    {
        if (Input.GetKey(KeyCode.W))
        {
            // 이동 방향을 넘겨주면 MoveController에서 IMovable 인터페이스를 통해 이동 로직 호출
            moveController.Move(Vector3.forward);
        }
    }
}
```

위 코드에서 <span style="color:brown">'IMovable'</span> 인터페이스를 선언하고, <span style="color:brown">'MoveController' 클래스</span>에서 <span style="color:brown">'IMovable' 인터페이스</span>에 의존하도록 구현하였다. <span style="color:blue">'Player' 클래스</span>에서는 <span style="color:brown">'IMovable' 인터페이스</span>를 구현하고, <span style="color:brown">'MoveController' 클래스</span>를 이용하여 이동을 제어 하였다!<br>
그러면 <span style="color:blue">'Player' 클래스</span>가 <span style="color:brown">'MoveController' 클래스</span>에 직접 의존하지 않고, 추상화된 <span style="color:brown">'IMovable' 인터페이스</span>에 의존하도록 구현된다! 왜냐? 위에서 설명한 것과 같이, <span style="color:brown">'MoveController' 클래스</span>는 <span style="color:brown">'IMovable' 인터페이스</span>에 의존하고 있기 때문이다. 결론적으로 <span style="color:brown">'IMovable' 인터페이스</span>의 구현이 변경되어도 <span style="color:blue">'Player' 클래스</span>의 수정이 필요하지 않게 된다!
