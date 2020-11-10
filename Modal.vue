<template>
  <div>
    <button @click="modalAtivo = !modalAtivo">Login</button>
    <transition name="modal">
      <div v-show="modalAtivo" class="modal-wrapper" @click="sairModal">
        <div class="modal">
          <h1>Login</h1>
          <form>
            <label for="email">E-mail</label>
            <input type="email" name="email" id="email" />
            <label for="senha">Senha</label>
            <input type="password" name="senha" id="senha" />
            <input type="submit" value="Entrar" />
          </form>
        </div>
      </div>
    </transition>
  </div>
</template>
<script>
export default {
  data() {
    return {
      modalAtivo: false,
    };
  },
  methods: {
    sairModal({ currentTarget, target }) {
      if (currentTarget === target) this.modalAtivo = false;
    },
  },
};
</script>
<style lang="css">
* {
  box-sizing: border-box;
}
body {
  font-family: monospace;
}
h1 {
  margin: 0px 0px 20px 0px;
}
.modal-wrapper {
  position: fixed;
  width: 100vw;
  height: 100vh;
  top: 0px;
  left: 0px;
  background: rgba(0, 0, 0, 0.4);
  overflow-y: scroll;
}
.modal {
  background: #cacaba;
  border-radius: 8px;
  padding: 20px;
  max-width: 400px;
  margin: 120px auto 0 auto;
  border: 8px solid #a1733f;
  z-index: 10;
}
label {
  display: block;
  margin-bottom: 5px;
}
input,
button {
  width: 100%;
  border: 4px solid #c9985d;
  outline: none;
  padding: 15px 10px;
  font-size: 1rem;
  margin-bottom: 20px;
}
input[type="submit"],
button {
  width: 200px;
  background: #801f12;
  color: #fff;
  cursor: pointer;
  text-transform: uppercase;
  font-size: 1rem;
  font-family: monospace;
  transition: filter 0.3s;
}
input[type="submit"]:hover,
button:hover {
  filter: brightness(80%);
}

.modal-enter,
.modal-leave-to {
  opacity: 0;
}
.modal-enter-active,
.modal-leave-to {
  transition: opacity 0.3s;
}

.modal-enter-to .modal {
  animation: slide 0.3s;
}
.modal-leave-to .modal {
  animation: slide 0.3s reverse;
}

@keyframes slide {
  from {
    transform: translate3d(0, -40px, 0);
  }
  to {
    transform: translate3d(0, 0px, 0);
  }
}
</style>