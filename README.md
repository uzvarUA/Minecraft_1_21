# Minecraft_1_21
```JavaScript
import React, { useState } from "react";
import { StyleSheet, Text, View } from "react-native";

const App = () => {
  const [armorStand, setArmorStand] = useState(null);

  const handleArmorStandClick = () => {
    if (!armorStand) {
      const armorStand = new ArmorStand();
      armorStand.setLocation(0, 0, 0);
      armorStand.setRotation(0, 0, 0);
      armorStand.setCustomName("Броненосець");
      armorStand.setHealth(200);

      // Додати броню
      armorStand.setItemInHand(0, new ItemStack(Material.IRON_BARDING));
      armorStand.setItemInOffHand(0, new ItemStack(Material.IRON_BARDING));

      // Додати щит
      armorStand.setItemInHand(1, new ItemStack(Material.SHIELD));

      setArmorStand(armorStand);
    } else {
      armorStand.destroy();
      setArmorStand(null);
    }
  };

  return (
    <View style={styles.container}>
      <Text style={styles.title}>Броненосець</Text>
      {armorStand && (
        <View style={styles.armorStand}>
          <Text style={styles.armorStandName}>{armorStand.customName}</Text>
        </View>
      )}
      <TouchableOpacity onPress={handleArmorStandClick}>
        <Text style={styles.button}>Створити броненосець</Text>
      </TouchableOpacity>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: "center",
    justifyContent: "center",
  },
  title: {
    fontSize: 24,
    fontWeight: "bold",
  },
  armorStand: {
    position: "absolute",
    top: 0,
    left: 0,
    width: 1,
    height: 1,
  },
  armorStandName: {
    fontSize: 16,
    color: "white",
  },
  button: {
    padding: 10,
    backgroundColor: "blue",
    borderRadius: 5,
  },
});

export default App;
```
