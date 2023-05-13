# OCP (Open-Close Principle)

• 정의 : 클래스, 모듈(함수나 변수 또는 클래스를 모아 놓은 파일) 등의 소프트웨어 객체는 확장에 대해 열려있어야 하고, 수정에 대해서는 닫혀 있어야 한다는 원칙!

```cs
// 무기를 나타내는 인터페이스
public interface IWeapon
{
    void Fire();
}

// 총 클래스
public class Gun : IWeapon
{
    public void Fire()
    {
        // 총을 발사하는 코드
    }
}

// 칼 클래스
public class Knife : IWeapon
{
    public void Fire()
    {
        // 칼을 사용하는 코드
    }
}

// 플레이어 캐릭터를 클래스
public class Player : MonoBehaviour
{
    // 무기를 담당하는 변수
    private IWeapon weapon;

    // 무기 설정 메서드 -> 매개변수로 Gun 혹은 Knife를 받을 수 있다!
    public void SetWeapon(IWeapon weapon)
    {
        this.weapon = weapon;
    }

    // 무기 사용 메서드
    public void UseWeapon()
    {
        weapon.Fire();
    }
}
```

OCP를 지키기 위해서는 기존의 코드를 변경하지 않고 새로운 기능을 추가할 수 있도록 설계해야 한다! 이를 위해서는 <span style="color:brown">인터페이스(interface)</span>나 <span style="color:brown">추상 클래스(abstract)</span>와 같은 추상화된 개념에 의존해야 한다!
위 코드에서와 같이 플레이어 캐릭터가 총을 발사하는 기능을 구현하는 코드가 있을 때, 새로운 종류의 무기가 추가될 때에도 기존 코드를 변경하지 않고 <span style="color:brown">IWeapon 인터페이스</span>를 구현하는 새로운 클래스를 추가하면 된다!
