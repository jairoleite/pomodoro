<template>
  <div class="layout-pomodoro">
    <div class="container">
      <header>
        <div class="logo">
          <q-icon name="check_circle" size="28px" color="white" />
          <span>Pomodoro</span>
        </div>
        <div class="actions">
          <q-btn
            outline
            size="12px"
            class="q-mr-sm"
            icon="insert_chart"
            style="color: white;"
            label="Report"
          />
          <q-btn
            outline
            size="12px"
            class="q-mr-sm"
            icon="settings"
            style="color: white;"
            label="Setting"
          />
          <q-btn outline size="12px" icon="perm_identity" style="color: white;" label="Login" />
        </div>
      </header>

      <div class="main">
        <div class="block-central">
          <div class="top-buttons">
            <span class="top-buttons-selected">Pomodoro</span>
            <span>Short Break</span>
            <span>Long Break</span>
          </div>

          <div class="display">
            <span>25:00</span>
          </div>

          <button>
            <span>START</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Pomodoro",
  data() {
    return {};
  },
};
</script>

<style>
.layout-promodoro {
  display: flex;
  flex-direction: column;
  align-items: center;

  width: 100%;
  height: 100vh;
  background-color: #f05a56;
}

.layout-promodoro > .container {
  width: 45%;
  height: 200px;
  margin-top: 5px;
}

.container > header {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

header > .logo {
  display: flex;
  flex-direction: row;
  align-items: center;

  font-family: "Varela Round", sans-serif;
}

header > .logo > span {
  font-size: 19px;
  margin-left: 2px;
  color: white;
  font-weight: 800;
}

.container > .main {
  display: flex;
  flex-direction: column;
  align-items: center;

  width: 100%;
  height: 100px;
  margin-top: 20px;
  border-top: 1px solid #da524e;
}

.block-central {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 15px;

  width: 75%;
  margin-top: 30px;
  background-color: #f16e6a;
}

.block-central > .top-buttons > span {
  font-family: "Varela Round", sans-serif;
  font-size: 16px;
  margin-right: 10px;
  padding: 3px;
  border-radius: 7px;
  color: white;
}

.top-buttons-selected {
  background-color: #d15e5c;
}

.block-central > .display {
  font-family: "Varela Round", sans-serif;
  font-size: 130px;
  font-weight: bold;
  color: #da524e;
}

.block-central > button {
  background: none;
  border: 1px solid white;
  background-color: white;
  width: 200px;
  height: 60px;
  outline: none;
  cursor: pointer;
  border-radius: 5px;
  border-bottom: 7px solid rgb(225, 225, 225);
}

.block-central > button > span {
  font-family: "Varela Round", sans-serif;
  font-size: 22px;
  font-weight: 800;
  color: #da524e;
}
</style>
