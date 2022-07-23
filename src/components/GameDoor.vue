<template>
  <div class="door-area">
    <div
      class="door-frame"
      :class="isSelected && 'selected'"
      @click="closeDoor"
    >
      <GameGift v-if="isOpen && hasGift" />
    </div>
    <div class="door" v-if="!isOpen" @click="selectDoor">
      <div class="door-number">
        {{ number }}
      </div>
      <div class="door-handle" @click="openDoor"></div>
    </div>
  </div>
</template> 

<script>
import GameGift from "./GameGift";

export default {
  components: {
    GameGift,
  },

  props: {
    number: {},
    hasGift: { type: Boolean },
  },

  data: function () {
    return {
      isOpen: false,
      isSelected: false,
    };
  },

  methods: {
    selectDoor() {
      this.isSelected = !this.isSelected;
    },

    openDoor() {
      this.isOpen = !this.isOpen;
      this.isSelected = false;
    },

    closeDoor() {
      this.isOpen = false;
    },
  },
};
</script>

<style>
.door-area {
  width: 180px;
  height: 300px;
  position: relative;
}

.door-frame {
  width: 100%;
  height: 100%;
  border: 5px solid #2e1200;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: end;
}

.door-frame.selected {
  border-color: #ffc31e;
}

.door {
  position: absolute;
  top: 5px;
  bottom: 5px;
  left: 5px;
  right: 5px;
  background: #572300;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem 0.8rem 0;
}

.door-number {
  font-size: 1.8rem;
}

.door-handle {
  width: 15px;
  height: 15px;
  border-radius: 50px;
  border: none;
  outline: none;
  background: #ffc31e;
  margin-top: 30%;
  align-self: start;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
}

.door-handle:hover {
  filter: brightness(0.9);
}
</style>