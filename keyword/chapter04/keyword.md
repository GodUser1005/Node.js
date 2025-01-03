### ES(ECMA Script)
- ECMA International 에서 다양한 기술의 호환성을 위한 규격을 정하는데 ECMA-262의 기술 규격을 따르는 표준화된 스크립트 언어를 말한다.
- 이 같은 규격이 탄생한 배경을 간단히 요약하면 넷스케이프사가 먼저 Javascript를 개발을 했고 이에 후발 주자로 MS가 Javascript와 비슷하고 적당히 호환 되는 JScript를 개발 하였다. 그러나 시간이 지날 수록 둘 사이의 호환이 안되는 문제가 발생하자 이를 위해 스크립트언어에 대한 규격을 정해놓음으로써 호환이 가능하도록 한 것이라 보면 된다.

##

### ES6(ES2015+)

#### ES5에서 ES6로의 주요 변화점
<br>

**1. const, let**
   - 자바스크립트에서는 var로 변수를 선언하였지만 ES6에서 var대신 const, let을 사용하도록 하였다. 

     ```
     if(true){
        var x = 3;
     }
     console.log(x);
     ```   
     위 코드를 실행하면 잘 작동 됨을 알 수 있는데 var가 함수 스코프의 범위를 갖는다

     하지만 위 코드에서 var를 const로 바꾸면 해당 코드는 실행이 되지않고 에러가 발생한다.
     ```
     if(true){
        const x = 3;
     }
     console.log(x);
     ```   
     그 이유는 const, let 모두 블록 스코프의 범위를 갖기 때문에 해당 블록에서 선언이 되면 블록 바깥에서는 내부에서 선언 된 걸 알 수가 없다.

- const는 변수선언 이름에서 알 수 있듯이 한 번 어떤 값을 할당을 하게되면 다른 값으로 재할당이 불가하다. 즉 상수의 의미를 가진다고 볼 수 있다. 또한 선언을 하게되면 그와 동시에 초기화를 해줘야 한다.

  let은 일반 변수처럼 선언과 동시에 초기화를 진행해주지 않아도 되고, 어떤 값으로 할당을 했어도 다른 값으로 재할당이 가능하다.

  따라서 const는 다른 값으로 재할당이 되지 않을 때만 사용하면되고 나머지 재할당이 필요해진다면 let을 사용하면 된다.

<br>

**2. 템플릿 문자열(리터럴)**

- '내용', "내용" 다음과 같이 문자열은 작은 따옴표와 큰 따옴표로 나타내었는데 따옴표 뿐만아니라 `(백틱) 이라는 걸 감싸는 형태도 문자열을 표현할 수 있다.
- 백틱표현의 특징은 백틱안에 변수를 넣을 수 있다. 
  ```
  const num3 = 1;
  const num2 = 2;
  const result2 = 2;
  const string2 = `${num3} 곱하기 ${num2}는 ${result2}`
  ```
  위 코드처럼 백틱안에 ${변수명} 이렇게 변수를 문자열 안에 넣을 수 있다.

<br>

**3. 객체 리터럴**
  - 객체의 메서드에 함수를 연결할 때 :(콜론) 과 function을 붙이지 않아도 되도록 했습니다.
    ```
    // 이전 문법
    var oldObject = {
      sayJs: function() {
      }
    };

    // ES6 문법
    var oldObject = {
      sayJs() {
      }
    };
    ```

  - 객체에서 속성명과 변수명이 동일한 경우에는 한번만 써도 되도록 했습니다.
    ```
    const name = 'Link';
    const age = 26;
    // 이전 문법
    var oldObject = { name: name, age: age};
    // ES6 문법
    var newObject = {name, age};
    ```

  - 객체의 속성명을 동적으로 생성이 가능한데 이전에는 객체 리터럴 바깥에서 생성을 해줬어야 했는데 ES6이후로는 객체리터럴 안에서 속성명을 동적으로 선언이 가능해졌습니다.
    ```
    var oldObject = {
      //ES6 에서 가능해짐
      [es+6]: 'fantastic',
    };
    // 이전문법
    oldObject[es+6] = 'fantastic'
    ```

<br>

**4. 화살표 함수**
  - 기존의 function도 사용이 가능하고 =>를 통해 화살표 함수를 만들수 있습니다.
    ```
    function add1(x,y) {
      return x+y;
    }
    
    const add2 = (x,y) => {
      return x+y;
    }

    const add3 = (x,y) => x+y;

    const add4 = (x,y) => (x+y);
    ```
    위 네가지의 add는 모두 같은 기능을 하는 함수이고 다음과 같이 화살표 함수로 표현이 가능합니다.

  - function과 arron function의 차이점은 this바인딩 방식에 차이가 있습니다.
    ```
    var relationship1 = {
      name: 'zero',
      friends: ['nero', 'hero', 'xero'],
      logFriends: fucntion() {

        // 아래 forEach에서의 함수와 logFriends 함수의 스코프가 달라 this가 다르므로 아래처럼 that이라는 변수를 통해 this를 아래 함수에 전달해줘야 한다

        var that = this;
        this.friends.forEach(function(friend) {
          console.log(that.name, friend);
        });
      },
    };
    relationship1.logFriends();

    ```

     ```
    const relationship2 = {
      name: 'zero',
      friends: ['nero', 'hero', 'xero'],
      logFriends() {

        // 다음과 같이 아래에 화살표 함수를 이용하면 상위 스코프의 this가 그대로 하위 스코프로 물려받기 때문에 this를 간접적으로 접근하지 않고 쓸 수 있다.

        this.friends.forEach(friend => {
          console.log(this.name, friend);
        });
      },
    };
    relationship1.logFriends();

    ```

<br>

**5. 구조 분해 할당**

  - 예시 1

    ```
    const candyMachine = {
      status: {
        name: 'node',
        count: 5,
      },
      getCandy() {
        this.status.count--;
        return this.status.count;
      },
    };
    
    // 아래가 구조분해할당 방법
    const { getCandy , status: {count} } = candyMachine;
    ```
  
  - 예시 2

    ```
    export const bodyToUser = (body) => {
      // 아래 코드가 구조분해할당
      const {email, name, gender, address} = body;

      return {
        email: email,
        name: name,
        gender: gender,
        address: address,
      };
    };
    ```

<br>

**6. 프로미스**

  - 자바스크립트나 노드는 비동기를 자주 접하는데, 이벤트 리스너를 사용시 콜백함수를 자주 사용한다.

  - 하지만 ES2015부터 자바스크립트와 노드의 API들이 콜백 대신 프로미스(Promise)기반으로 재구성 되었고, 이덕분에 콜백 지옥 현상을 극복할 수 있게 되었다.

  - 프로미스 사용법
    ```
    const condition = true; // true이면 resolve, false이면 reject
    // 아래가 promise 사용법
    const promise = new Promise((resolve, reject) => {
      if (condition) {
        resolve('성공');
      } else {
        reject('실패');
      }
    });
    // 위 코드가 프로미스 객체를 생성하고 그안에 시간이 다소 걸리는 I/O를 다루는 코드나 함수를 실행하는 코드를 넣고 성공 한 결과를 resolve에 넣고 실패하면 그 결과를 reject에 넣게 된다.

    // 다른코드 실행

    promise
      .then((message) => {
        console.log(message);
      })
      .catch((error) => {
        console.log(error);
      })
      .finally(() => {  // 무조건 실행
        console.log('무조건');
      });
    
    //위 생성한 프로미스 객체에서의 결과를 다른 코드가 실행하고 나중에 받을 수 있도록 한 것이 promise의 특징입니다.
    ```

  - 프로미스는 then이나 catch에서 또 다른 then을 붙일 수도 있습니다.

    ```
    promise
      .then((message) => {
        return new Promise((resolve, reject) => {
          resolve(message);
        });
      })
      .then((message2) => {
        console.log(message2);
        return new Promise((resolve, reject) => {
          resolve(message2);
        });
      })
      .then((message3) => {
        console.log(message3);
      })

      .catch((error) => {
        console.log(error);
      });
    ```

  - 위 코드 처럼 첫번째 then의 결과로 새로운 프로미스 객체를 리턴해주면 그 객체를 then으로 또받아 잇는 형식으로 만들어지며 위 방식을 활용해서 여러 콜백을 병렬적으로 연결할 수 있습니다.

  - 콜백함수를 프로미스로 바꿀 수 있다고 했는데 아래 코드가 그 예시 입니다.

    ```
    function findAndSaveUser(Users) {
      Users.findOne({}, (err,user) => { // 첫번째 콜백
        if(err){
          return console.log(err);
        }
        user.name = 'zero';
        user.save((err) => {  // 두번째 콜백
          if(err) {
            return console.error(err);
          }
          Users.findOne({gender: 'm'}, (err, user) => { // 세번째 콜백
            // 생략
          });
        });
      });
    }
    ```
  
  - 위 코드는 콜백함수가 3번 중첩되어있고 콜백함수가 나올 때마다 코드의 깊이가 더 깊어진다. 이를 프로미스로 사용하면 다음과 같다.

    ```
    function findAndSaveUser(Users) {
      Users.findOne({})
        .then((user) => {
          user.name = 'zero';
          return user.save();
        })
        .then((user) => {
          return Users.findOne({gender: 'm'});
        })
        .then((user) => {
          // 생략
        })

        .catch((err) => {
          console.error(err);
        });
    }
    ```

  - 아까 콜백함수의 깊어짐보다 덜 깊게 코드가 짜여진걸 볼수 있다. 그리고 위 경우는 findOne 이라는 함수와 save 함수내에 promise 객체를 갖고있다고 가정해야한다.

  - 프로미스는 위처럼 꼬리를 무는 방식으로 여러개 처리하는 기법말고도 한꺼번에 여러개의 프로미스를 처리하는 방식도 존재합니다.

    ```
    const promise1 = Promise.resolve('성공1);
    const promise2 = Promise.resolve('성공2');
    Promise.all([promise1, promise2])
      .then((result) => {
        console.log(result); // ['성공1', '성공2']
      })
      .catch((err) => {
        console.error(err);
      });
    ```
  - Promise.all을 사용하면 프로미스들을 한꺼번에 처리하고 에러처리도 한꺼번에 해준다
  - 위 코드에서 promise1과 promise2 모두가 성공하면 then으로 가게되고 둘중에 하나라도 에러가 발생하면 catch문이 실행된다. 그러나 둘중 어떤 프로미스가 reject 되었는지는 알 수 없다.

  - 만약 여러 프로미스를 실행하는데 어떤 프로미스에서 에러가 발생했는지를 알고싶다면 Promise.all 대신에 Promise.allSettled를 사용하면 된다.

  - 추가로 Node 16버전부터 reject된 Promise에 catch를 달지 않으면 UnhandledPromiseRejection 에러가 발생하므로 프로미스에 catch 메서드를 붙이는 것을 권장한다.






<br>

**7. ES Module**

  - Module이란 다른 자바스크립트 파일에서 선언된 함수나 객체를 현재의 자바스크립트파일에서 재사용하기 위한 방식을 말한다.

  - 기존에는 CommonJs 모듈을 사용 했는데 이는 자바스크립트의 표준은 아니었고 다음과 같이 사용이 되었다.
    ```
    const { odd ,even } = require('./var');
    ```

    위 코드의 의미는 현재 디렉토리의 var.js라는 파일의 module.exports의 객체에서 odd, even 속성을 할당 하라는 의미입니다.

    CommonJs 모듈방식에서는 require를 통해 모듈을 가져오고 , exports, module.exports를 통해 모듈을 내보내고 싶은 형식으로 내보낼 수 있습니다.

- ES Module이 표준으로 자리 잡으면서 문법에도 변화가 생겼는데 기존의 require가 import로 exports가 export로 module.exports가 export default로 바뀌었습니다. 위 코드를 ES module 형식으로 바꾸면 아래와 같습니다.

    ```
    import {odd, even} from './var.mjs';
    ```

<br>



#### ES6가 중요한 이유
   - 기존 문법에서 많은 획기적인 새로운 요소들이 추가가 되었고 현대 웹 애플리케이션 개발의 다양한 영역에서 활용될 뿐 아니라 빠르게 개발을 할 수 있도록 가독성과 유지 보수성 측면에서 다른 버전들 보다 많은 향상이 이뤄 졌기 때문이다.

##

### 프로젝트 아키텍처

#### 프로젝트 아키텍처가 중요한 이유

- 프로젝트의 규모가 작다면 임의로 아키텍처를 구조화 하지 않고 할 수 있다.

- 하지만 프로젝트 규모가 협업의 규모이거나 확장될 여지가 많은 프로젝트라면 무엇보다 아키텍처를 짜는 것이 중요하다.

- 프로젝트의 규모가 커지는데 아키텍처가 없다면 로직이 빈번이 바뀔때마다 데이터 의존성도 빈번이 바뀌게 되고 어떤 스크립트 파일이 어떤 기능을 위한 건지 알아볼수도 없고 협업에서 다른사람의 스크립트가 무엇을 위한 것인지 알 수없어 시간적 손해가 매우크다

- 이러한 문제를 해결하려면 프로젝트 시작부터 아키텍처를 견고하게 설정하는 것이 중요하다
  
#### Service-Oriented Architecture
- 사용자에게 제공하는 서비스를 위주로 비즈니스 애플리케이션을 생성하는 소프트웨어 개발 방식을 말한다.

- 웹 애플리케이션에서 사용자에게 서비스를 제공할 때는 다음과 같은 단계로 이뤄진다.

- 사용자가 도메인에 URI를 통해 서비스를 요청을 하게 되면 URI마다 라우팅을 통해 분기를 해주고 요청이 서버에 도착을 하면 서버는 요청을 받아 자체적인 비즈니스 로직을 이용해 사용자가 요구하는 데이터를 사용자에게 응답해주게 된다.

- 이러한 서비스 일련의 과정을 아키텍처로 구분한 것이 서비스 지향 아키텍처이다.

- routing, controller, service, 데이터 접근 처리 총 4단계로 나누는 것이 일반적이다.

- routing 에서는 사용자의 요청에 대한 URI를 일일이 하나씩 대응하려면 번거롭기 때문에 비슷한 요청은 하나의 그룹으로 묶어서 요청을 받도록 하는 것을 말한다.

   예를 들어, 사용자가 본인의 정보에 관련된 서비스를 요청하는 것은 user.route가 요청을 받게 되는 것이고 사용자가 가게에 대한 서비스를 요청하는 것은 store.route에서 요청을 받도록 하는 것을 말한다.

- controller 에서는 사용자의 요청을 받으면 실제 로직을 처리하는 service와 연결을 해주는 처리를 담당한다. 라우팅에서 걸러져온 각 요청을 받아 service로 입력 데이터를 전달 해주고 비즈니스 로직에서 처리한 내용을 바탕으로 사용자에게 요청에 맞게 데이터를 전달 해 주는 것을 말한다.

- service는 개발하는 소프트웨어의 핵심 로직을 담당하는 부분이며 controller로 부터 받은 입력과 데이터베이스상의 데이터를 통해 정보를 만들고 이를 controller에 넘겨주어 응답하도록 하는 부분이다.

- 데이터 접근 처리(DAO) 에서는 실제로 데이터들이 모여있는 DB는 웹 애플리케이션과 분리가 되어있다. 이렇게 분리된 DB를 접근 해서 원하는 데이터를 가져오거나 혹은 DB에 데이터를 쓸 때 필요한 부분을 따로 DAO에서 처리하도록 하는 것이 이 단계이다.


#### MVC 패턴

- 디자인 패턴중 Model, View, Controller 패턴을 말한다.

- Model은 데이터와 비즈니스 로직을 처리하는 부분이며 server상에서 해당 웹 애플리케이션의 핵심기능을 수행하고, 필요한 데이터들을 가공하는 부분을 말합니다.

- View는 사용자에게 보여지는 부분으로 UI 부분입니다. Model을 통해 데이터가 가공되거나 생성되거나 삭제등이 이뤄지고 그러한 내용중 사용자에게 제공해야하는 부분만 view로 전달을 해서 view를 통해 사용자에게 보여주는 것을 말합니다.

- Controller는 Model에서 로직을 처리하기위해 사용자로부터 입력을 받도록 해주고 해당 입력에 따라 Model에서 처리를 해주고 이 결과를 view에게 전달할 때 controller가 Model로 부터 전달을 해줍니다. 즉 controller는 model의 입력과 출력에 연결이 되어있고 view는 controller의 입력과 출력에 연결이 되어있습니다.

- 웹 개발에 있어서 View에 해당하는 부분에서의 개발을 Front-end, controller, model에 대한 부분에서의 개발을 Back-end로 나눕니다.


##

### 비즈니스 로직

- 웹 애플리케이션을 개발 하는데 있어서 Service단에서 진행하는 모든 행위들을 말하며 이 부분은 웹 애플리케이션을 사용하는 사용자는 알 수 없습니다. 이 부분을 통해 사용자의 요청에 따라 적절한 결과물을 도출해야 하므로 개발자는 이 로직을 가장 핵심적으로 잘 짜야합니다.

- UMC에서의 SOA 아키텍쳐 에서는 Service 에서 처리하는 모든것을 말합니다.

##

### DTO(Data transfer Object)

- 우리의 웹 애플리케이션은 사용자 입장에서는 하나의 서버로만 보여지지만 실제로 내부에는 view, model, controller와 같이 나누어져 있고 model 상에서도 데이터접근, 로직처리 등 여러 layer로 구성되어 있음을 위 아키텍처를 통해 알 수 있었다.

- 이러한 layer는 나름 분리가 되어있기에 layer간의 데이터를 서로 주고받기 위해서는 각 layer가 수용할 수 있는 데이터의 형태로 변환을 해줘야한다. 이러한 데이터를 어떤 객체에 담아서 다른 layer에게 보내는 데 이러한 역할을 하는 것이 DTO이다.

- layer를 controller, service, DAO 로 나누게 된다고 가정하면
  controller에서는 사용자의 입력을 받아 service로 데이터를 보내줘야하는 데 이때 DTO를 생성해서 service로 보내준다. 그 뿐 아니라 service로 부터 데이터를 받고 이를 UI 즉 Frontend로 보내줄 때도 DTO가 사용된다.(혹은 json으로 그냥 넘겨주기도 한다.)

  service에서는 controller로 부터 받은 입력을 처리하고 사용자에게 보여줄 데이터만 따로 뽑아 DTO로 만들어 controller에게 보내준다. 이러한 측면에서 DTO를 통해 사용자의 데이터를 보호해주는 측면도 볼 수 있다.

  DAO에서는 service에서 요청 쿼리를 보내면 해당 데이터 중 필요한 부분만을 DTO에 저장하여 service가 해당 데이터로 처리할 수 있게 데이터를 보내준다.

  만약 데이터를 받는 layer에서는 DTO를 이용하지않으면 유효성검사를 따로 해주어야 하는데 이 작업을 DTO를 통해 가능하게 해준다고 볼 수도 있다.