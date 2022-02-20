Vue
node modules -> npm library
package.json -> 
main -> 구동 => 전역으로 import 해줌

main.js에 전역으로 선언할 컴포넌트를 넣을때는
Vue.component('내가만들컴포넌트 이름', import해준 component의 이름)

router -> component 라우팅
store -> 전역

vue-cli-plugin
상태관리 프레임워크, 컴포넌트 기반 vuetify - bootstrap 같은?

npm run build -> 배포를 위한 command

import (component이름 아무거나) from (vue file 경로)
외부의 vue file을 가져오기 위함

---

부모 자식간의 component 정보 전달

1. 부모에게서 전달하고자 하는값을 v-bind를 이용해 저장
<component: nameofchild="name">(부모 html부분 template안에서)

2. component vue파일(자식)
export default{
props:["nameofchild"],
}




부모 자식간의 component를 이용한 정보 전달시

만약에, 자식에서 부모에게 받은값을 바꾸게된다 -> 부모는 값이? 안바뀜!!!
부모의 값을 바꿔주려면 어떻게 해야할까? emit!

자식이 부모에게 신호를 보내주려면!
this.$emit("child") <-string을 넣어줌
this.$emit("child",user) <- user이라는 object나 인자들을 넣을 수 있음

부모가 자식 emit받으려면
@child= "parents" <- parents는 메소드임
parents 메소드에서는 저 user의 값을 이용해 부모 객체의 값을 수정 가능함




자식과 자식간의 정보 전달

1. main.js에 event bus를 추가해준다
export const eventBus = new Vue()

2. 받을 component에서 import
import { eventBus } from '../main'

3. 메소드 부분에서 eventBus를 불러옴

4. 다른 component에서 data 부분에 eventbus에서 받은 값을 받음
같은 동일한 level의 component이기 때문에, emit처럼 @받음! 이렇게 할 수 없다!



여러 컴포넌트에서 불러와 재사용 
Mixin

만약 mixin 메소드와 component안의 메소드의 이름이 같다면?
누가 실행될까??

mixin 내 함수보다, 진짜 component안의 메소드가 먼저 실행이된다!

즉, mixin이 먼저 실행되며, 결국에는 component에 선택권한이 있어서 수정이 가능!

mixin -> component data
mixin -> component data
