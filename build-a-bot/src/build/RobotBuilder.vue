<template>
  <div class="content">
    <button class="add-to-cart" @click="addToCart()">Add to Cart</button>
    <div class="top-row">
      <div class="top part">
        <div class="robot-name">
          {{ selectedRobot.head.title }}
          <span v-if="selectedRobot.head.onSale" class="sale">Sale !</span>
        </div>
        <img :src="selectedRobot.head.src" title="head" />
        <button @click="selectPrevHead()" class="prev-selector">&#9668;</button>
        <button @click="selectNextHead()" class="next-selector">&#9658;</button>
      </div>
    </div>
    <div class="middle-row">
      <div class="left part">
        <img :src="selectedRobot.leftArm.src" title="left arm" />
        <button @click="selectPrevLeftArm()" class="prev-selector">&#9650;</button>
        <button @click="selectNextLeftArm()" class="next-selector">&#9660;</button>
      </div>
      <div class="center part">
        <img :src="selectedRobot.torso.src" title="center part" />
        <button @click="selectPrevTorso()" class="prev-selector">&#9668;</button>
        <button @click="selectNextTorso()" class="next-selector">&#9658;</button>
      </div>
      <div class="right part">
        <img :src="selectedRobot.rightArm.src" title="right arm" />
        <button @click="selectPrevRightArm()" class="prev-selector">&#9650;</button>
        <button @click="selectNextRightArm()" class="next-selector">&#9660;</button>
      </div>
    </div>
    <div class="bottom-row">
      <div class="bottom part">
        <img :src="selectedRobot.base.src" title="bases" />
        <button @click="selectPrevLeg()" class="prev-selector">&#9668;</button>
        <button @click="selectNextLeg()" class="next-selector">&#9658;</button>
      </div>
    </div>
    <div>
      <h1>Cart</h1>
      <table>
        <thead>
          <tr>
            <th>Robot</th>
            <th class="cost"></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(robot, index) in cart" :key="index">
            <td>
              {{ robot.head.title }}
            </td>
            <td class="cost">{{ robot.cost }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import availableParts from "../data/parts";

export default {
  name: "RobotBuilder",
  data() {
    return {
      availableParts,
      cart: [],
      selectedHeadIndex: 0,
      selectedTorsoIndex: 0,
      selectedLegIndex: 0,
      selectedLeftArmIndex: 0,
      selectedRightArmIndex: 0,
    };
  },
  computed: {
    selectedRobot() {
      return {
        head: availableParts.heads[this.selectedHeadIndex],
        leftArm: availableParts.arms[this.selectedLeftArmIndex],
        rightArm: availableParts.arms[this.selectedRightArmIndex],
        torso: availableParts.torsos[this.selectedTorsoIndex],
        base: availableParts.bases[this.selectedLegIndex],
      };
    },
  },
  methods: {
    addToCart() {
      const robot = this.selectedRobot;
      const cost =
        robot.head.cost +
        robot.leftArm.cost +
        robot.rightArm.cost +
        robot.torso.cost +
        robot.base.cost;
      console.log({ ...robot, cost });
      this.cart.push({ ...robot, cost });
    },
    selectNextHead() {
      console.log("selectNextHead called");
      if (this.selectedHeadIndex === this.availableParts.heads.length - 1) {
        this.selectedHeadIndex = 0;
        return;
      }
      this.selectedHeadIndex += 1;
    },
    selectPrevHead() {
      console.log("selectPrevHead called");
      if (this.selectedHeadIndex === 0) {
        this.selectedHeadIndex = this.availableParts.heads.length - 1;
        return;
      }
      this.selectedHeadIndex -= 1;
    },
    selectNextTorso() {
      console.log("selectNextTorso called");
      if (this.selectedTorsoIndex === this.availableParts.torsos.length - 1) {
        this.selectedTorsoIndex = 0;
        return;
      }
      this.selectedTorsoIndex += 1;
    },
    selectPrevTorso() {
      console.log("selectPrevTorso called");
      if (this.selectedTorsoIndex === 0) {
        this.selectedTorsoIndex = this.availableParts.torsos.length - 1;
        return;
      }
      this.selectedTorsoIndex -= 1;
    },
    selectNextLeg() {
      console.log("selectNextLeg called");
      if (this.selectedLegIndex === this.availableParts.bases.length - 1) {
        this.selectedLegIndex = 0;
        return;
      }
      this.selectedLegIndex += 1;
    },
    selectPrevLeg() {
      console.log("selectPrevLeg called");
      if (this.selectedLegIndex === 0) {
        this.selectedLegIndex = this.availableParts.bases.length - 1;
        return;
      }
      this.selectedLegIndex -= 1;
    },
    selectNextLeftArm() {
      console.log("selectNextLeftArm called");
      if (this.selectedLeftArmIndex === this.availableParts.arms.length - 1) {
        this.selectedLeftArmIndex = 0;
        return;
      }
      this.selectedLeftArmIndex += 1;
    },
    selectPrevLeftArm() {
      console.log("selectPrevLeftArm called");
      if (this.selectedLeftArmIndex === 0) {
        this.selectedLeftArmIndex = this.availableParts.arms.length - 1;
        return;
      }
      this.selectedLeftArmIndex -= 1;
    },
    selectNextRightArm() {
      console.log("selectNextRightArm called");
      if (this.selectedRightArmIndex === this.availableParts.arms.length - 1) {
        this.selectedRightArmIndex = 0;
        return;
      }
      this.selectedRightArmIndex += 1;
    },
    selectPrevRightArm() {
      console.log("selectPrevRightArm called");
      if (this.selectedRightArmIndex === 0) {
        this.selectedRightArmIndex = this.availableParts.arms.length - 1;
        return;
      }
      this.selectedRightArmIndex -= 1;
    },
  },
};
</script>

<style>
.part {
  position: relative;
  width: 165px;
  height: 165px;
  border: 3px solid #aaa;
}
.part img {
  width: 165px;
}
.top-row {
  display: flex;
  justify-content: space-around;
}
.middle-row {
  display: flex;
  justify-content: center;
}
.bottom-row {
  display: flex;
  justify-content: space-around;
  border-top: none;
}
.head {
  border-bottom: none;
}
.left {
  border-right: none;
}
.right {
  border-left: none;
}
.left img {
  transform: rotate(-90deg);
}
.right img {
  transform: rotate(90deg);
}
.bottom {
  border-top: none;
}
.prev-selector {
  position: absolute;
  z-index: 1;
  top: -3px;
  left: -28px;
  width: 25px;
  height: 171px;
}
.next-selector {
  position: absolute;
  z-index: 1;
  top: -3px;
  right: -28px;
  width: 25px;
  height: 171px;
}
.center .prev-selector,
.center .next-selector {
  opacity: 0.8;
}
.left .prev-selector {
  top: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.left .next-selector {
  top: auto;
  bottom: -28px;
  left: -3px;
  width: 144px;
  height: 25px;
}
.right .prev-selector {
  top: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  top: auto;
  bottom: -28px;
  left: 24px;
  width: 144px;
  height: 25px;
}
.right .next-selector {
  right: -3px;
}
.robot-name {
  position: absolute;
  top: -25px;
  text-align: center;
  width: 100%;
}
.sale {
  color: red;
}
.content {
  position: relative;
}

.add-to-cart {
  position: absolute;
  right: 30px;
  width: 220px;
  padding: 3px;
  font-size: 16px;
}

td,
th {
  text-align: left;
  padding: 5px 20px 5px 5px;
}
.cost {
  text-align: right;
}
</style>
