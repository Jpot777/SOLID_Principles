# LSP (Liskov Substitution Principle)

• 정의 : 상속에 대한 개념으로, 부모 클래스가 들어갈 자리에 자식 클래스를 넣어도 잘 구동되어야 한다는 원칙!
부모 클래스와 자식 클래스 간의 상속 관계를 잘 정의해야 한다! 자식 클래스는 부모 클래스가 가진 모든 기능을 포함하면서도 새로운 기능을 추가할 수 있어야 한다.

```cs
// 캐릭터를 나타내는 부모 클래스
public class Character : MonoBehaviour
{
    // 캐릭터의 이동 메서드
    public virtual void Move(Vector3 direction)
    {
        // 이동하는 코드
    }
}

// 플레이어 캐릭터 클래스
public class Player : Character
{
    // 플레이어 캐릭터 이동 메서드
    public override void Move(Vector3 direction)
    {
        // 플레이어 캐릭터가 이동하는 코드
    }
}

// 몬스터 캐릭터 클래스
public class Monster : Character
{
    // 몬스터 캐릭터 이동 메서드
    public override void Move(Vector3 direction)
    {
        // 몬스터 캐릭터가 이동하는 코드
    }
}
```

위 코드와 같이 작성함으로서, <span style="color:brown">'Player'</span> 클래스와 <span style="color:brown">'Monster'</span> 클래스 모두 <span style="color:brown">'Character'</span> 클래스의 인스턴스를 대체할 수 있다! 예시는 아래 코드와 같다!

```cs
public class GameController : MonoBehaviour
{
    // 캐릭터를 나타내는 Character 타입의 변수
    private Character character;

    private void Start()
    {
        // 1. Player 클래스의 인스턴스를 Character 타입 변수에 할당
        character = new Player();

        // 2. 몬스터 클래스의 인스턴스를 Character 타입 변수에 할당
        // character = new Monster();
    }

    private void Update()
    {
        // 이동 방향 설정
        Vector3 direction = new Vector3(1f, 0f, 0f);

        // 캐릭터 이동
        character.Move(direction);
    }
}

```
