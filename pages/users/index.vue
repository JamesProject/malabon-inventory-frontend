<template>
  <div>
    <!-- Confirm delete dialog -->
    <div class="w-full">
      <v-dialog v-model="deleteDialog" persistent max-width="290">
        <template v-slot:activator="{ on, attrs }">
          <v-btn color="primary" dark v-bind="attrs" v-on="on" right>
            Add User
          </v-btn>
        </template>
        <v-card>
          <v-card-title class="text-h5">
            Use Google's location service?
          </v-card-title>
          <v-card-text>Let Google help apps determine location. This means sending anonymous location data to Google,
            even when no apps are running.</v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="green darken-1" text @click="dialog = false">
              Disagree
            </v-btn>
            <v-btn color="green darken-1" text @click="dialog = false">
              Agree
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>
    <v-data-table v-model="selected" :headers="headers" :items="desserts" :single-select="singleSelect" item-key="name"
      show-select class="elevation-1">
      <template v-slot:item.active="{ item }">
         <v-checkbox
          v-model="item.active"
        ></v-checkbox>
      </template>
      <template v-slot:item.actions="{ item }">
        <v-icon small class="mr-2" @click="editItem(item)">
          mdi-pencil
        </v-icon>
        <v-icon small @click="deleteItem(item)">
          mdi-delete
        </v-icon>
      </template>
    </v-data-table>



  </div>
</template>
<script>
  export default {
    data() {
      return {
        singleSelect: false,
        selected: [],
        deleteDialog: false,
        headers: [{
            text: 'Full Name',
            align: 'start',
            sortable: true,
            value: 'name',
          },
          {
            text: 'Active',
            value: 'active'
          },
          {
            text: 'Roles',
            value: 'roles'
          },
          {
            text: 'Created at',
            value: 'created_at'
          },
          {
            text: 'Updated at',
            value: 'updated_at'
          },
          {
            text: 'Actions',
            value: 'actions'
          },
        ],
        desserts: [{
          "name": "Alameda Sweedy",
          "active": false,
          "role": [{},
            {}
          ],
          "created_at": "3/9/2021",
          "updated_at": "10/31/2021",
          "actions": false
        }, {
          "name": "Yardley Rouge",
          "active": true,
          "role": [{},
            {},
            {},
            {}
          ],
          "created_at": "10/1/2021",
          "updated_at": "10/20/2021",
          "actions": false
        }, {
          "name": "Angus Woolforde",
          "active": true,
          "role": [{},
            {},
            {}
          ],
          "created_at": "3/23/2021",
          "updated_at": "2/9/2021",
          "actions": true
        }, {
          "name": "Grier Dorsett",
          "active": false,
          "role": [{},
            {},
            {},
            {},
            {}
          ],
          "created_at": "3/19/2021",
          "updated_at": "7/19/2021",
          "actions": false
        }, {
          "name": "Gunther Adnams",
          "active": true,
          "role": [{},
            {},
            {},
            {},
            {}
          ],
          "created_at": "4/29/2021",
          "updated_at": "9/24/2021",
          "actions": false
        }, {
          "name": "Lindi Undrell",
          "active": false,
          "role": [{},
            {},
            {},
            {}
          ],
          "created_at": "3/16/2021",
          "updated_at": "8/15/2021",
          "actions": true
        }, {
          "name": "Sharity Pyke",
          "active": true,
          "role": [{},
            {},
            {},
            {},
            {}
          ],
          "created_at": "10/3/2021",
          "updated_at": "11/28/2020",
          "actions": true
        }, {
          "name": "Ethelyn Greenhouse",
          "active": true,
          "role": [{}],
          "created_at": "4/22/2021",
          "updated_at": "12/6/2020",
          "actions": false
        }, {
          "name": "Jonah Rickerby",
          "active": true,
          "role": [

          ],
          "created_at": "5/22/2021",
          "updated_at": "1/13/2021",
          "actions": true
        }, {
          "name": "Ham Radbourn",
          "active": false,
          "role": [{},
            {}
          ],
          "created_at": "8/14/2021",
          "updated_at": "12/23/2020",
          "actions": false
        }, {
          "name": "Harmonia Malyan",
          "active": true,
          "role": [

          ],
          "created_at": "2/16/2021",
          "updated_at": "2/26/2021",
          "actions": true
        }, {
          "name": "Kassia Montague",
          "active": false,
          "role": [{}],
          "created_at": "3/17/2021",
          "updated_at": "11/23/2021",
          "actions": true
        }, {
          "name": "Gilly Ramelot",
          "active": false,
          "role": [{},
            {},
            {}
          ],
          "created_at": "11/18/2021",
          "updated_at": "10/1/2021",
          "actions": false
        }, {
          "name": "Tilda Segar",
          "active": true,
          "role": [{}],
          "created_at": "10/27/2021",
          "updated_at": "3/13/2021",
          "actions": true
        }, {
          "name": "Bev Popley",
          "active": false,
          "role": [{}],
          "created_at": "9/17/2021",
          "updated_at": "9/29/2021",
          "actions": false
        }, {
          "name": "Brigit Lumm",
          "active": true,
          "role": [{},
            {},
            {},
            {}
          ],
          "created_at": "5/1/2021",
          "updated_at": "2/25/2021",
          "actions": false
        }, {
          "name": "Nikos Casel",
          "active": true,
          "role": [

          ],
          "created_at": "11/12/2021",
          "updated_at": "6/13/2021",
          "actions": true
        }, {
          "name": "Brandy Penquet",
          "active": false,
          "role": [{},
            {},
            {}
          ],
          "created_at": "7/15/2021",
          "updated_at": "9/14/2021",
          "actions": true
        }, {
          "name": "Tamara Trickett",
          "active": false,
          "role": [{}],
          "created_at": "5/25/2021",
          "updated_at": "2/13/2021",
          "actions": true
        }, {
          "name": "Bourke Bover",
          "active": true,
          "role": [{}],
          "created_at": "12/22/2020",
          "updated_at": "5/8/2021",
          "actions": true
        }],
      }
    },
    methods: {
      editItem() {
        this.deleteDialog = true
      }
    }
  }

</script>
