# test
T1


import React, {useState} from 'react';
import {createBottomTabNavigator} from '@react-navigation/bottom-tabs';
import {Text, StyleSheet, View} from 'react-native';
import Icon from 'react-native-vector-icons/AntDesign';
import {Picker} from '@react-native-picker/picker';

const Tab = createBottomTabNavigator();

function FoodScreen() {
  const [selectedLanguage, setSelectedLanguage] = useState();

  return (
    <View style={styles.fp}>
      <Picker
        selectedValue={selectedLanguage}
        onValueChange={(itemValue, itemIndex) =>
          setSelectedLanguage(itemValue)
        }>
        <Picker.Item label="Java" value="java" />
        <Picker.Item label="JavaScript" value="js" />
      </Picker>
    </View>
  );
}

function PlaceScreen() {
  return <Text style={styles.fp}>Tourist Attractions</Text>;
}

function PathScreen() {
  return <Text style={styles.route}>Pathway</Text>;
}

function Home() {
  return (
    <Tab.Navigator initialRouteName="Food">
      <Tab.Screen
        name="Food"
        component={FoodScreen}
        options={{
          title: '맛집',
          tabBarIcon: ({color, size}) => (
            <Icon name="rest" color={'black'} size={30} />
          ),
        }}
      />
      <Tab.Screen
        name="Place"
        component={PlaceScreen}
        options={{
          title: '관광지',
          tabBarIcon: ({color, size}) => (
            <Icon name="isv" color={'black'} size={30} />
          ),
        }}
      />
      <Tab.Screen
        name="Path"
        component={PathScreen}
        options={{
          title: '최적경로',
          tabBarIcon: ({color, size}) => (
            <Icon name="enviroment" color={'black'} size={30} />
          ),
        }}
      />
    </Tab.Navigator>
  );
}

const styles = StyleSheet.create({
  fp: {
    flex: 1,
    backgroundColor: 'white',
  },
  route: {
    flex: 1,
    backgroundColor: 'white',
  },
  mypage: {
    flex: 1,
    backgroundColor: 'white',
  },
});

export default Home;
