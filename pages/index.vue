<template>
    <div class="container-fluid">
        <div class="row my-5">
            <div class="col-lg-6">
                <nuxt-link to="/pengunjung/tambah">
                    <div class="card bg-kunjung rounded-5">
                        <div class="card-body">
                            <h2>Pengujung</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>
            <div class="col-lg-6">
                <nuxt-link to="/buku">
                    <div class="card bg-buku rounded-5">
                        <div class="card-body">
                            <h2>Cari Buku</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>
        </div>
        <h2 style="margin: 30px;"><strong>STATISTIK</strong></h2>
        <div class="container-fluid">
            <div class="row justify-content-evenly rounded-5">
                <div class="col-5">
                    <div class="raccing">
                        <NuxtLink to="/pengunjung">
                            <h2>{{ visitors.length }} pengunjung</h2>
                        </NuxtLink>
                    </div>
                </div>
                <div class="col-5">
                    <div class="raccing">
                        <h2>9 Buku </h2>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card {
    height: 250px;
    box-shadow: 1px 1px 10px #424242;
}

.card.bg-kunjung {
    background-image: url("../assets/img/kunjung.jpg");
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
}

.card.bg-buku {
    background: url("../assets/img/bg-home-cari-buku.jpg") no-repeat center center;
    background-size: cover;
}

.raccing {
    height: 200px;
    box-shadow: 1px 1px 10px;
    border-radius: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: cadetblue;
}

.raccing1 {
    height: 200px;
    box-shadow: 1px 1px 10px;
    border-radius: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: aquamarine;
}
</style>

<script setup>

const supabase = useSupabaseClient()
const visitors = ref([])


const getPengunjung = async () => {
    const { data, error } = await supabase.from('pengunjung').select(`*, keanggotaan(*), keperluan(*)`)
    if (data) visitors.value = data
    }

onMounted(() => {
    getPengunjung()
})



</script>