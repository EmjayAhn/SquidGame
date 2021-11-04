# Assert

`assert`는 어떤 조건을 테스트해 에러를 발생시키는 디버깅 보조도구이다. 조건이 참이면 아무 일도 일어나지 않고, 거짓이면 `AssertionError`가 발생한다.

```python
def apply_discount(price, discount_rate):
    dc_price = int(price * (1 - discount_rate))
    assert 0 <= dc_price <= price, 'price out of range'
    
    return dc_price
   
shoes = {'name': 'Loafer',
        'price': 14900}
```



위 신발을 25% 할인하려고 하면 아래와 같이 할인된 가격이 반환된다.

```python
apply_discount(shoes['price'], 0.25)
```

Out: 11175



그러나 만약 200% 할인하겠다고 하면 에러가 발생한다.

```python
apply_discount(shoes['price'], 2)
```

![image](https://user-images.githubusercontent.com/44221498/140320625-260b75e8-ccf8-4914-becd-5fc19bbb6d2f.png)



Traceback을 통해 에러가 발생한 코드가 몇 번째 줄인지, 즉 에러의 근본 원인을 금방 찾을 수 있기 때문에 assert를 사용하면 디버깅이 쉬워진다.

**주의할 점: `assert` 문의 첫 번째 인자로 튜플을 전달하게 되면, 튜플이 비어있지 않은 이상 파이썬에서 항상 참이기 때문에 어떤 경우에도 에러가 발생되지 않는다.*

```python
assert(1==2, 'this should fail')
```

1은 2가 아니지만 아무 에러가 발생되지 않는다. 아래와 같이 써줘야 한다.

```python
assert 1==2, 'this works'
```

![image](https://user-images.githubusercontent.com/44221498/140321010-ab3227b8-25c6-49c9-97e6-870cf297b889.png)



