# 네임드튜플(named tuple)

파이썬의 자료형 nameduple에 대해 알아보자. 우선 tuple과는 어떤 점이 다를까?

**`tuple`**

- 튜플은 불변이므로 일단 생성되면 수정할 수 없다.

- 튜플에 저장된 데이터를 가져오려면 정수 인덱스를 사용해야 한다.

- 튜플에 저장된 개별 속성에는 이름을 지정할 수 없어 가독성에 악영향을 준다.

  

**`namedtuple`**

- 일반 튜플과 같이 변경 불가능한 컨테이너다. 네임드튜플 객체의 모든 속성은 '한 번만 쓰고 여러 번 읽는다' 는 원칙을 따른다.
- 그러나 일반 튜플과는 달리 **고유한(사람이 읽을 수 있는) 식별자를 통해 각 객체에 접근할 수 있다.**
- 말 그대로 "이름을 가진 튜플"이라고 보면 된다.
- 내부적으로 일반 파이썬 클래스로 구현되지만 메모리 사용량은 일반 클래스보다 좋고 일반 튜플만큼 메모리 면에서 효율적이다.



### 튜플과 네임드튜플의 예

```python
# 튜플
tup = ('color', 'mileage')
tup[0]
```

Out: 'color'

```python
from collections import namedtuple
# 네임드튜플
Car = namedtuple('Car', 'color mileage')
```



위 예시에서 생성한 `namedtuple` 객체의 첫 번째 인자로 쓰인 문자열 'Car'은 *타입명(typename)*이라고 하며, 이는 `namedtuple` 함수를 호출해 생성되는 새 클래스의 이름이 된다. 이 클래스명은 `namedtuple`이 자동으로 생성하는 docstring과 `__repr__` 구현에 사용된다.

두 번째 인자로 전달한 값 'color mileage'는 클래스의 속성들에 해당한다. 내부에서 `split()`을 적용하므로 띄어쓰기 단위로 여러 속성을 한 번에 전달할 수 있다.

물론 아래와 같이 속성들을 직접 리스트로 나눠 전달할 수도 있다. 이렇게 하면 가독성도 좋고 코드 수정도 쉬워진다.

```python
Car = namedtuple('Car', [
    'color', 
    'mileage',
])
```



이렇게 선언하고 나면 아래와 같이 새로운 Car 객체를 만들 수 있다. **네임드튜플은 마치 Car 클래스를 수동으로 정의하고 'color'와 'mileage' 생성자가 주어진 것처럼 동작**한다. 네임드튜플의 객체 값에는 식별자를 통해서도 접근할 수 있고, 인덱스를 통해서도 접근할 수 있다.

```python
# 식별자를 통한 접근
my_car = Car('red', 1000)
my_car.color
```

Out: 'red'

```python
# 인덱스를 통한 접근
my_car = Car('red', 1000)
my_car[0]
```

Out: 'red'



네임드튜플 객체는 `tuple()` 로 감싸 속성들을 튜플로 간편하게 변환할 수 있고, 함수 인자를 풀어주는 `*` 연산자도 동작한다.

```python
tuple(my_car)
```

Out: ('red', 1000)

```python
print(*my_car)
```

Out: red 1000



> ***"네임드튜플은 파이썬에서 불변클래스를 수동으로 정의할 때 사용할 수 있는 메모리 효율적인 지름길이다."***



### 네임드튜플 상속

네임드튜플은 일반 파이썬 클래스로 구현되므로 네임드튜플 객체를 다른 클래스에서 상속받아 메서드를 추가할 수 있다.

```python
Car = namedtuple('Car', ['color', 'mileage'])

# 네임드튜플을 클래스에서 상속
class MyCarWithMethods(Car):
    def hexcolor(self):
        if self.color == 'red':
            return '#ff0000'
        else:
            return '#000000'
          
c = MyCarWithMethods('red', 1500)
c.hexcolor()          
```

Out: '#ff0000'



이보다 더 쉬운 방식도 있다. 네임드 튜플의 `_fields` 속성을 사용하는 것이다.

```python
Car._fields
```

Out: ('color', 'mileage')



```python
# _fields 속성을 이용한 상속
ElectricCar = namedtuple('ElectricCar', Car._fields + ('charge', ))
electric_car = ElectricCar('white', 2000, 100)
electric_car
```

Out: ElectricCar(color='white', mileage=2000, charge=100)



위와 같이 직접적으로 Car 네임드튜플에 정의된 필드들을 가져오고 거기에 새로운 필드를 추가함으로써 Car의 속성들을 상속한 새로운 namedtuple을 생성할 수 있다.



### 내장도우미 메서드

네임드튜플 인스턴스는 `_fields` 속성 외에도 몇 가지 유용한 도움 메서드를 제공한다.
도움 메서드는 모두 `_`로 시작하지만 네임드튜플에서 이 모든 메서드는 는 공개 인터페이스에 포함되므로 사용할 수 있다.



- **`_asdict()`** : 네임드튜플의 내용을 딕셔너리(`OrderedDict` 형태)로 반환한다. `json.dumps()`를 이용해 json형식으로 반환할 때 유용하다.

  ```python
  my_car._asdict()
  ```

  Out: OrderedDict([('color', 'red'), ('mileage', '1000')])

  ```python
  json.dumps(my_car._asdict())
  ```

  Out: '{"color": "red", "mileage": "1000"}'

- **`_replace()`** : 네임드튜플 객체의 얕은 복사본을 생성하고 속성 값을 대체할 수 있다.

  ```python
  my_car._replace(color='blue')
  ```

  Out: Car(color='blue', mileage='1000')

