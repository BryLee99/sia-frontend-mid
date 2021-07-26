<template>
    <div>
        <b-button v-b-modal.addFriend variant="primary">Add Friend</b-button>

        <b-modal id="addFriend" title="Friend" ok-title="Save" @ok="onSubmit">
            <form action="#">

                <b-form-group
                    label="UID"
                    label-for="uid">
                    
                    <b-form-input id="uid" v-model="friend.uid" trim></b-form-input>
                </b-form-group>

                <b-form-group
                    label="User Name"
                    label-for="user_name">
                    
                    <b-form-input id="user_name" v-model="friend.user_name" trim></b-form-input>
                </b-form-group>

                <b-form-group
                    label="Nick Name"
                    label-for="nick_name">
                    
                    <b-form-input id="nick_name" v-model="friend.nick_name" trim></b-form-input>
                </b-form-group>

            </form>
        </b-modal>
    </div>
</template>

<script>
export default {
    data() {
        return {
            friend: {}
        }
    },
    methods:{
        async onSubmit(){
            this.$axios.post('/api/friends/', this.friend)
            .then((res)=>{
                if(res.status==202){
                    alert('Successfully added a friend')
                    this.$emit('onAdd')
                }
            })
        }
    }
    
}
</script>