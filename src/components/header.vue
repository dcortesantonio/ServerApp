<template>
    <nav class="navbar fixed-top navbar-expand-lg  navbar-dark bg-dark">

        <a class="navbar-brand" href="#">Server Application</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarTogglerDemo03" aria-controls="navbarTogglerDemo03" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarTogglerDemo03">
            <ul class="navbar-nav">
                <li class="nav-item active">
                    <a class="nav-link" ><router-link to="history"><p class="text-white bg-dark"><i class="fa fa-fw fa-home"></i> Home</p>
                    </router-link> </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#"><router-link to="history"><p class="text-white bg-dark"><i class="fa fa-history" aria-hidden="true"></i>
                        History of Searches</p>
                     </router-link> </a>
                </li>
                <li class="nav-item">
                    <a class="nav-link" href="#"><router-link to="search"><p class="text-white bg-dark"><i class="fa fa-fw fa-search"></i>Search</p>
                    </router-link> </a>
                </li>
            </ul>

        </div>
    </nav>
</template>

<script>
   /* import Search from "./components/Search"
    import User from "./components/User"
    import HelloWorld from "./components/HelloWorld"
    export default {
        name: 'App',
        components:{
            'users':User,
            'home': HelloWorld,
            //'app-header': Header,
            'search': Search
        }
    }*/
</script>

<style>

</style>