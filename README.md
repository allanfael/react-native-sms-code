# react-native-sms-code
The purpose of this package is provide SMS verification codes on Android devices.
## Installation

```sh
npm install react-native-sms-code
yarn add react-native-sms-code
```

## Usage

```js
import {
registerBroadcastReceiver,
codeReceived,
unregisterBroadcastReceiver,
} from 'react-native-sms-code';


// ...
const [code, setCode] = React.useState('');

const handleCodeReceived = async () => {
  try {
    const otpCode = await codeReceived();
    setCode(otpCode);
  } catch (e) {
    console.log('error', e);
  }
};

React.useEffect(() => {
  registerBroadcastReceiver();

  handleCodeReceived();

  return () => {
    unregisterBroadcastReceiver();
  };

}, []);


return (
  <View style={styles.container}>
    <Text>Code:</Text>
    <TextInput
      value={code}
      onChangeText={setCode}
      underlineColorAndroid="#3333"
    />
  </View>
);

const styles = StyleSheet.create({
  container: {
  flex: 1,
  justifyContent: 'center',
  padding: 8,
  },
  box: {
  width: 60,
  height: 60,
  marginVertical: 20,
  },
  textInput: {
  width: '100%',
  },
});

```
## Demonstration
<img src="./example/src/assets/sms-code.gif" width="260" height="550" />

## Extra Parameter
### codeLength()
The length of the code to be received. Default is 6.
```js

## License

MIT
