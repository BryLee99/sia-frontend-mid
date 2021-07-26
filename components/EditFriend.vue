<template>
    <div>
        
        <b-modal id="editFriend" title="Friend" ok-title="Save" @ok="onSubmit">
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
    props: {
        friend: {}
    },


    methods: {
        async onSubmit(){
            await this.$axios.put('/api/friends/' + this.friend.id, this.friend)
            .then((res)=>{
                if(res.status==202) {
                    alert('Update Succesful!!')
                    console.log(this.friend)
                }
            })
            .catch((err)=>{
                alert(err.message)
            })
        }
    }
}
</script>