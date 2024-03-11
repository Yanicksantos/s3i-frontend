<template>
    <div>
    <v-dialog max-width="900">
        <template v-slot:activator="{ props: activatorProps }">
            <v-btn
            v-bind="activatorProps"
            icon="mdi-chevron-right" 
            variant="text"
            ></v-btn>
        </template>

        <template v-slot:default="{ isActive }">
            <v-card height="500" style="overflow-y: hidden;">
                <v-row>
                    <v-col cols="5" >
                        <v-img src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460" cover height="500"></v-img>
                    </v-col>
                    <v-col cols="7">
                       
                    </v-col>
                </v-row>
            </v-card>
        </template>
    </v-dialog>
    </div>
</template>