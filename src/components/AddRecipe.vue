
<template>
  <form class="form" @submit.prevent='submit'>
    <h1>Добавить позицию</h1>
    <div v-if="visible">
        <div class="input">
            <input type='text' placeholder="именование" v-model="title">
        </div>
        <div class="input">
            <input type='text' placeholder="описание" v-model="descr">
        </div>
    </div>

    <div class="buttons">
        <button class="btn" type="submit" :disabled="!valid">Показать</button>
        <button class="btn secondary" type="button" @click="toggle">
            {{ visible ? 'Убрать' : 'Показать' }} форму
        </button>
    </div>
  </form>
</template>


<script>
export default {
    props: {
        onAdd: {
            type: Function,
            required: true
        }
    },
    data() {
        return {
            title: '',
            descr: '',
            visible: true
        }
    },
    methods: {
        toggle() {
            this.visible = !this.visible
        },
        submit() {
            const recipe = {
                title: this.title.trim(),
                descr: this.descr.trim(),
                id: Date.now().toString()
            }

            this.title = this.descr = ''

            this.onAdd(recipe)
        }
    },
    computed: {
        valid() {
            return this.title.trim() && this.descr.trim()
        }
    }
}
</script>

<style>
    .form {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 1rem;
    border: 1px solid #eee;
    margin-bottom: 1rem;
    box-shadow: 0px 0px 10px #aa6363;
  }
  .form h1 {
    margin: 0;
    margin-bottom: 1rem;
  }
  .input {
    margin-bottom: 1rem;
  }
  .input input {
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 5px 8px;
    width: 400px;
    outline: none;
    transition: all .4s;
  }
  .input input:focus {
      box-shadow: 0px 0px 5px rgb(90, 104, 231);
      transition: all .4s;
  }
  .buttons {
    width: 400px;
    display: flex;
    justify-content: space-around;
  }
</style>


