## Installation
```
yarn add vue-bulma-notifications
```

## Usages
```
Vue.component('notification', require('vue-bulma-notifications'))
```

```
<notification>
    You have been notified!
</notification>
```

#### Available props
* `auto-close-after` - Number | Will auto close after X milliseconds
* `is-closeable` - Boolean | If the notification can be closed or not
* `remember` - Boolean | If the closed state should be remembered on the device. Will save to local storage.
* `type` - String | Bulma classes. E.g.: `is-primary`, `is-success`, `is-danger`, etc.
