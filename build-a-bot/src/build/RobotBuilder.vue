<template>
  <div>
    <div class="top-row">
      <div class="top part">
        <img v-bind:src="availableParts.heads[selectedHeadIndex].src" title="head" />
        <button v-on:click="selectPrevHead()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextHead()" class="next-selector">&#9658;</button>
      </div>
    </div>
    <div class="middle-row">
      <div class="left part">
        <img v-bind:src="availableParts.arms[selectedLeftArmIndex].src" title="left arm" />
        <button v-on:click="selectPrevLeftArm()" class="prev-selector">&#9650;</button>
        <button v-on:click="selectNextLeftArm()" class="next-selector">&#9660;</button>
      </div>
      <div class="center part">
        <img v-bind:src="availableParts.torsos[selectedTorsoIndex].src" title="center part" />
        <button v-on:click="selectPrevTorso()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextTorso()" class="next-selector">&#9658;</button>
      </div>
      <div class="right part">
        <img v-bind:src="availableParts.arms[selectedRightArmIndex].src" title="right arm" />
        <button v-on:click="selectPrevRightArm()" class="prev-selector">&#9650;</button>
        <button v-on:click="selectNextRightArm()" class="next-selector">&#9660;</button>
      </div>
    </div>
    <div class="bottom-row">
      <div class="bottom part">
        <img v-bind:src="availableParts.bases[selectedLegIndex].src" title="bases" />
        <button v-on:click="selectPrevLeg()" class="prev-selector">&#9668;</button>
        <button v-on:click="selectNextLeg()" class="next-selector">&#9658;</button>
      </div>
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
      selectedHeadIndex: 0,
      selectedTorsoIndex: 0,
      selectedLegIndex: 0,
      selectedLeftArmIndex: 0,
      selectedRightArmIndex: 0,
    };
  },
  methods: {
    selectNextHead() {
      console.log("selectNextHead called");
      if (this.selectedHeadIndex === this.availableParts.heads.length - 1) return;
      this.selectedHeadIndex += 1;
    },
    selectPrevHead() {
      console.log("selectPrevHead called");
      if (this.selectedHeadIndex === 0) return;
      this.selectedHeadIndex -= 1;
    },
    selectNextTorso() {
      console.log("selectNextTorso called");
      if (this.selectedTorsoIndex === this.availableParts.torsos.length - 1) return;
      this.selectedTorsoIndex += 1;
    },
    selectPrevTorso() {
      console.log("selectPrevTorso called");
      if (this.selectedTorsoIndex === 0) return;
      this.selectedTorsoIndex -= 1;
    },
    selectNextLeg() {
      console.log("selectNextLeg called");
      if (this.selectedLegIndex === this.availableParts.bases.length - 1) return;
      this.selectedLegIndex += 1;
    },
    selectPrevLeg() {
      console.log("selectPrevLeg called");
      if (this.selectedLegIndex === 0) return;
      this.selectedLegIndex -= 1;
    },
    selectNextLeftArm() {
      console.log("selectNextLeftArm called");
      if (this.selectedLeftArmIndex === this.availableParts.arms.length - 1) return;
      this.selectedLeftArmIndex += 1;
    },
    selectPrevLeftArm() {
      console.log("selectPrevLeftArm called");
      if (this.selectedLeftArmIndex === 0) return;
      this.selectedLeftArmIndex -= 1;
    },
    selectNextRightArm() {
      console.log("selectNextRightArm called");
      if (this.selectedRightArmIndex === this.availableParts.arms.length - 1) return;
      this.selectedRightArmIndex += 1;
    },
    selectPrevRightArm() {
      console.log("selectPrevRightArm called");
      if (this.selectedRightArmIndex === 0) return;
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
</style>
