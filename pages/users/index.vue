<template>
<div>
  <v-data-table
    v-model="selected"
    :headers="headers"
    :items="desserts"
    :single-select="singleSelect"
    item-key="name"
    show-select
    class="elevation-1"
  >
    <template v-slot:item.actions="{ item }">
      <v-icon
        small
        class="mr-2"
        @click="editItem(item)"
      >
        mdi-pencil
      </v-icon>
      <v-icon
        small
        @click="deleteItem(item)"
      >
        mdi-delete
      </v-icon>
    </template>
  </v-data-table>


  <!-- Confirm delete dialog -->
  <v-dialog
      v-model="deleteDialog"
      persistent
      max-width="290"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="primary"
          dark
          v-bind="attrs"
          v-on="on"
        >
          Open Dialog
        </v-btn>
      </template>
      <v-card>
        <v-card-title class="text-h5">
          Use Google's location service?
        </v-card-title>
        <v-card-text>Let Google help apps determine location. This means sending anonymous location data to Google, even when no apps are running.</v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="green darken-1"
            text
            @click="dialog = false"
          >
            Disagree
          </v-btn>
          <v-btn
            color="green darken-1"
            text
            @click="dialog = false"
          >
            Agree
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
</div>
</template>
<script>
  export default {
    data () {
      return {
        singleSelect: false,
        selected: [],
        deleteDialog: false,
        headers: [
          {
            text: 'Full Name',
            align: 'start',
            sortable: true,
            value: 'name',
          },
          { text: 'Active', value: 'active' },
          { text: 'Roles', value: 'roles' },
          { text: 'Created at', value: 'created_at' },
          { text: 'Updated at', value: 'updated_at' },
          { text: 'Actions', value: 'actions' },
        ],
        desserts: [
          {
            name: 'James Ulip',
            active: '159',
            role: [1,2,3,4],
            created_at: 24,
            updated_at: 4.0,
            actions: false,
          },
          {
            name: 'John Doe',
            active: '159',
            role: 6.0,
            created_at: 24,
            updated_at: 4.0,
            actions: false,
          },
        ],
      }
    },
    methods:{
      editItem(){
        this.deleteDialog  = true
      }
    }
  }
</script>
