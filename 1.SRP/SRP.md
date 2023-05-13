# SRP (Single Responsibility Principle )

• 정의 : 모든 클래스는 하나의 책임만 가지며, 그 책임은 완전히 캡슐화 되어야 한다!
(응집도는 높고, 결합도는 낮은 프로그램)
클래스의 책임이 많아지면 내부 함수끼리 강한 결합을 발생하여
유지보수 비용이 증가하게 되므로 책임을 분리시킬 필요가 있다.

```cs
// 적 캐릭터를 제어하는 클래스
public class EnemyController : MonoBehaviour
{
    // 적 캐릭터의 이동과 회전을 담당하는 메서드
    public void MoveAndRotate()
    {
        // 1. 적 캐릭터를 이동시키는 코드
        // 2. 적 캐릭터를 회전시키는 코드
    }

    // 적 캐릭터의 공격을 담당하는 메서드
    public void Attack()
    {
        // 적 캐릭터의 공격을 실행하는 코드
    }

}

// 적 캐릭터의 AI를 구현하는 클래스
public class EnemyAI : MonoBehaviour
{
    // 적 캐릭터의 AI를 실행하는 메서드
    public void ExecuteAI()
    {
    // 적 캐릭터의 AI를 구현하는 코드
    }
}
