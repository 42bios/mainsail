<template>
    <v-card>
        <v-list-item>
            <v-list-item-avatar color="grey"><v-icon dark>mdi-exclamation-thick</v-icon></v-list-item-avatar>
            <v-list-item-content>
                <v-list-item-title class="headline">Machine Limits</v-list-item-title>
            </v-list-item-content>
        </v-list-item>
        <v-divider class="my-2"></v-divider>
        <v-card-text class="px-0 pt-0 pb-2 content">
            <v-row class="px-6" >
                <v-col sm-12>
                    <toolSlider label="VELOCITY" v-bind:target="max_velocity" :max="200" :extender="true" :extender-steps="100" command="SET_VELOCITY_LIMIT" attribute-name="VELOCITY=" class="mt-5" ></toolSlider>
                    <toolSlider label="ACCEL" v-bind:target="max_accel" :max="5000" :extender="true" :extender-steps="500" command="SET_VELOCITY_LIMIT" attribute-name="ACCEL=" class="mt-5" ></toolSlider>
                    <toolSlider label="DECEL" v-bind:target="max_accel_to_decel" :max="5000" :extender="true" :extender-steps="500" command="SET_VELOCITY_LIMIT" attribute-name="ACCEL_TO_DECEL=" class="mt-5" ></toolSlider>
                    <toolSlider label="SCV" v-bind:target="square_corner_velocity" :max="10" :extender="true" :extender-steps="5" command="SET_VELOCITY_LIMIT" attribute-name="SQUARE_CORNER_VELOCITY=" class="mt-5" ></toolSlider>
                </v-col>
            </v-row>
        </v-card-text>
    </v-card>
</template>

<script>
    import { mapState } from 'vuex'
    import toolSlider from '../../../inputs/ToolSlider'

    export default {
        components: {
            toolSlider
        },
        data: function() {
            return {

            }
        },
        computed: {
            ...mapState({
                max_velocity: state => state.printer.toolhead.max_velocity,
                max_accel: state => state.printer.toolhead.max_accel,
                max_accel_to_decel: state => state.printer.toolhead.max_accel_to_decel,
                square_corner_velocity: state => state.printer.toolhead.square_corner_velocity,
            })
        },
        methods: {

        }
    }
</script>