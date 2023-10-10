<template>
  <v-app>
    <v-container fluid class="text-center">
      <v-row>
        <v-col cols="4">
          <v-card class="task-list">
            <v-card-title color="error">
              A Fazer
              <v-icon
              end
              icon="mdi-alert"
              size="x-small"
              color="error"
              ></v-icon>
            </v-card-title>
            <v-divider></v-divider>
            <v-card-text>
              <v-list>
                <v-list-item v-for="(task, index) in toDoTasks" :key="index">
                  <v-list-item-content>
                    {{ task }}
                  </v-list-item-content>
                  <v-list-item-action>
                    <v-btn icon @click="moveTask(index, 'inProgress')">
                      <v-icon>mdi-arrow-right</v-icon>
                    </v-btn>
                  </v-list-item-action>
                </v-list-item>
              </v-list>
            </v-card-text>
            <v-card-actions>
              <v-col class="text-center">
                <v-btn
                @click="showTaskForm = true"
                >
                Criar Nova Tarefa
                </v-btn>
              </v-col>
              <v-dialog v-model="showTaskForm" persistent>
                <v-card>
                  <v-card-title>Criar Nova Tarefa</v-card-title>
                  <v-card-text>
                    <v-text-field v-model="newTask" label="Nome da Tarefa"></v-text-field>
                  </v-card-text>
                  <v-card-actions>
                    <v-btn @click="createNewTask">Salvar</v-btn>
                    <v-btn @click="showTaskForm = false">Cancelar</v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </v-card-actions>
          </v-card>
        </v-col>
        <v-col cols="4">
          <v-card class="task-list">
            <v-card-title>
              Em Progresso
              <v-icon
              end
              icon="mdi-clock-time-four"
              size="x-small"
              color="amber"
              ></v-icon>
            </v-card-title>
            <v-divider></v-divider>
            <v-card-text>
              <v-list>
                <v-list-item v-for="(task, index) in inProgressTasks" :key="index">
                  <v-list-item-content>
                    {{ task }}
                  </v-list-item-content>
                  <v-list-item-action>
                    <v-btn icon @click="moveTask(index, 'done')">
                      <v-icon>mdi-check</v-icon>
                    </v-btn>
                  </v-list-item-action>
                </v-list-item>
              </v-list>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="4">
          <v-card class="task-list">
            <v-card-title>
              Concluídas
              <v-icon
              end
              icon="mdi-checkbox-marked-circle"
              size="x-small"
              color="green"
              ></v-icon>
            </v-card-title>
            <v-divider></v-divider>
            <v-card-text>
              <v-list>
                <v-list-item v-for="(task, index) in doneTasks" :key="index">
                  <v-list-item-content>
                    {{ task }}
                  </v-list-item-content>
                  <v-list-item-action>
                    <v-btn icon @click="moveTask(index, 'inProgress')">
                      <v-icon>mdi-arrow-left</v-icon>
                    </v-btn>
                  </v-list-item-action>
                </v-list-item>
              </v-list>
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      toDoTasks: ['Tarefa 1', 'Tarefa 2', 'Tarefa 3'],
      inProgressTasks: [],
      doneTasks: [],
      newTask: '',
      showTaskForm: false,
    };
  },
  methods: {
    moveTask(index, category) {
      const task = this.toDoTasks.splice(index, 1)[0];
      if (category === 'inProgress') {
        this.inProgressTasks.push(task);
      } else if (category === 'done') {
        this.doneTasks.push(task);
      }
    },
    createNewTask() {
      if (this.newTask) {
        this.toDoTasks.push(this.newTask);
        this.newTask = '';
        this.showTaskForm = false; // Fechar o formulário após criar a tarefa
      }
    },
  },
};
</script>

<style>
.task-list {
  margin: 10px;
}
</style>
