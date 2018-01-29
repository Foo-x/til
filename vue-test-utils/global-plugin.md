# global plugin使用時のmount

vuex, vue-router, vuetifyなどglobalで使用しているpluginがある場合はmountしてもうまくいかない場合がある。

例: Vuetifyのコンポーネントに@click.nativeを設定していてtrigger("click")しても反応しない

以下の対応をする。
```js
import Foo from "foo"
import Vuetify from "vuetify"
import { mount, createLocalVue } from "@vue/test-utils"

const localVue = createLocalVue()
localVue.use(Vuetify)

const sut = mount(Foo, {
  localVue
})
```

なお、この場合はshallowだとエラーが出るのでmountにする。
