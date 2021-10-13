<template>
  <div class="container">

    <h2 class="text-center mt-5">My vue Todo App</h2>
    <!-- İnput-->
    <div class="d-flex">
      <input v-model="task" type="text" placeholder="Enter To do List" class="form-control">
      <button @click="SubmitSave" class="btn btn-warning rounded-0">Kaydet</button>
    </div>
    <!-- task tables-->
    <table class="table table-hover table-dark">
      <thead>
      <tr>
        <th scope="col">Görevler</th>
        <th scope="col">Durum</th>
        <th scope="col">Kontrol Edecek Kişi</th>
        <th scope="col" class="text-center">#</th>
        <th scope="col" class="text-center">#</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(product , task4) in tasks" :key="task4">
        <th>{{ product.name }}</th>
        <td><span @click="ChangeStatues(task4)" class="pointer">{{ product.status }}</span></td>
        <td>{{ product.author }}</td>
        <td>
          <div @click="updateTask(task4)" class="text-center">
            <span class="fa fa-pen">
            </span>
          </div>
        </td>
        <td>
          <div class="text-center" @click="deleteTask(task4)">
            <span class="fa fa-trash"></span

            ></div>
        </td>
      </tr>
      </tbody>
    </table>

  </div>
</template>

<script>
export default {
  name: "todoList",
  data() {
    return {
      task: 'Hello ibrahim abi',
      updatedTask: null,
      Statues:['Yapılacak','Yapılıyor','Yapıldı'],
      tasks: [
        {
          name: "To Do List Yapılacak Vue Js İle",
          status: "Yapılıyor",
          author: "Merve Anka"

        },
        {
          name: "İndirim Kodları Hazırlanacak",
          status: "Yapıldı",
          author: "Adeviye Şahin"

        },
        {
          name: "CSS Dersleri İzlenip İbrahim Verdiği Görevler Yapılacak",
          status: "Yapılıyor.",
          author: "İbrahim Akbaş"

        },
      ]
    }
  },
  methods: {
    SubmitSave() {
      if (this.task.length === 0) return;
      if (this.updatedTask === null) {
        this.tasks.push({
          name: this.task,
          status: 'Yapılacak',
          author: 'İbrahim Mestav',
        });
      }
      else {
        this.tasks[this.updatedTask].name=this.task;
        this.updatedTask=null;
      }

    },
    deleteTask(task4) {
      this.tasks.splice(task4, 1)
    },
    updateTask(task4) {
      this.task = this.tasks[task4].name;
      this.updatedTask = task4;

    },
    ChangeStatues(task4)
    {
    let newIndex =  this.Statues.indexOf(this.tasks[task4].status);
    if(++newIndex>2)
      newIndex=0;
    this.tasks[task4].status=this.Statues[newIndex];
    },
  }

}
</script>

<style scoped>

.pointer{
  cursor: pointer;
}
</style>
