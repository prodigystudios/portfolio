<template>
    <h1 class="center">Mina projekt!</h1>
    <div class="main-container">
        <div class="content-align" v-for="project in projects" :key="project.id">
            <router-link :to="'project/' + project.id">
                <div>
                    <h2>{{  project.projectName  }}</h2>
                    <img class="img-scale" :src="project.img" :alt="project.projectName">
                    <h3>{{  project.projectDescription  }}</h3>
                    <div class="icons-container">
                        <div class="aling-icons" v-for="(icon, index) in project.icons" :key="index">
                            <img class="scale-icon" :src="icon.icon">
                        </div>
                    </div>
                </div>
            </router-link>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            projects: [
                {
                    id: 0,
                    projectName: "Todo app",
                    projectDescription: "En att göra lista! Perfekt för dig som har många saker att inte glömma bort väldigt enkel att använda",
                    img: require("@/assets/testTodo.png"),
                    icons: [
                        {
                            icon: require("@/assets/icons/icons8-html-5-32.png"),
                        },
                        {
                            icon: require("@/assets/icons/icons8-css3-32.png"),
                        },
                        {
                            icon: require("@/assets/icons/icons8-sql-32.png"),
                        },
                        {
                            icon: require("@/assets/icons/icons8-c-sharp-logo-32.png"),
                        },
                        {
                            icon: require("@/assets/icons/icons8-.net-framework-32.png"),
                        },
                        {
                            icon: require("@/assets/logo.png"),
                        },
                    ]
                },
                {
                    id: 1,
                    projectName: "Blogg App",
                    projectDescription: "En enkel blogg sida där du kan skapa, redigera och ta bort inlägg",
                    img: require("@/assets/Blogg/SizeTest.png"),
                    icons: [
                        {
                            icon: require("@/assets/icons/icons8-html-5-32.png"),
                        },
                        {
                            icon: require("@/assets/icons/icons8-css3-32.png"),
                        },
                        {
                            icon: require("@/assets/icons/icons8-sql-32.png"),
                        },
                        {
                            icon: require("@/assets/icons/icons8-c-sharp-logo-32.png"),
                        },
                        {
                            icon: require("@/assets/logo.png"),
                        },
                    ]
                },
                {
                    id: 2,
                    projectName: "Brödernas Clone",
                    projectDescription: "En enkel clone av med en del av brödernas information och en meny",
                    img: require("@/assets/BrödernasClone/Home.png"),
                    icons: [
                        {
                            icon: require("@/assets/icons/icons8-html-5-32.png"),
                        },
                        {
                            icon: require("@/assets/icons/icons8-css3-32.png"),
                        },
                        {
                            icon: require("@/assets/logo.png"),
                        },
                    ]
                },
                {
                    id: 3,
                    projectName: "Webshop",
                    projectDescription: "En super enkel webshop! Där du kan se information om produkten med bilder",
                    img: require("@/assets/Webshop/Home.png"),
                    icons: [
                        {
                            icon: require("@/assets/icons/icons8-html-5-32.png"),
                        },
                        {
                            icon: require("@/assets/icons/icons8-css3-32.png"),
                        },
                        {
                            icon: require("@/assets/icons/icons8-sql-32.png"),
                        },
                        {
                            icon: require("@/assets/icons/icons8-c-sharp-logo-32.png"),
                        },
                        {
                            icon: require("@/assets/logo.png"),
                        },
                    ]
                },
                {
                    id: 4,
                    projectName: "Väder app",
                    projectDescription: "En enkel lite väder app där du kan se vädret idag och 7 dagar framöver",
                    img: require("@/assets/WheaterApp/Home.png"),
                    icons: [
                        {
                            icon: require("@/assets/icons/icons8-html-5-32.png"),
                        },
                        {
                            icon: require("@/assets/icons/icons8-css3-32.png"),
                        },
                        {
                            icon: require("@/assets/logo.png"),
                        },
                    ]
                },
            ],
        }
    },
}
</script>
    
<style scoped>
.center
{
    text-align: center;
}

.main-container
{
    display: grid;
    grid-template-columns: repeat(auto-fill, 246px);
    width: 100%;
    gap: 1em;
    margin-bottom: 20px;
}

.content-align
{
    border: 1px solid black;
    border-radius: 10px;
    gap: 50px;
    text-align: center;

}

.content-align h3
{
    height: 90px;
    padding: 0px 20px;
}

.content-align:hover
{
    outline: var(--clr-hover-link) solid 2px;
}

.content-align a
{
    color: black;
}

.content-align a:hover
{
    color: rgba(135, 206, 250, 0.7);
}

.icons-container
{
    display: flex;
    justify-content: center;
    height: 100%;
    margin: 10px 0px;
}

.scale-icon
{
    width: 32px;
}

.img-scale
{
    width: 100%;
    height: 115px;
    object-fit: contain;
}

@media (max-width: 425px)
{
    .main-container
    {
        display: grid;
        grid-template-columns: repeat(auto-fill, 400px);
        width: 100%;
        gap: 1em;
        margin-bottom: 20px;
    }
}
</style>