<template>
    <nav class="container" mb-4 mt-4>
        <div class="row">
            <div class="col-9"></div>
            <div class="col-3">
                <select class="custom-select" v-model="lang" @change="handleChange($event)">
                    <option value="en">EngLish</option>
                    <option value="vi">VietNam</option>    
                    <option value="de">Deutsh</option>                
                </select>
            </div>
        </div>
    </nav>
</template>

<script>
    export default{

        data: function(){
            const lang = localStorage.getItem('lang') || 'en';
            return {
                lang: lang
            }
        },

        methods: {
            handleChange(event){
                localStorage.setItem('lang', event.target.value);
                window.location.reload();
            }
        }
    };
</script>
