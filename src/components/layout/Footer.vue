<template>
    <footer class="page-footer">
        <div class="container">
            <div class="row">
                <div class="col l6 s12">
                    <h5 class="white-text">Vo Do List</h5>
                    <p class="grey-text text-lighten-4">To Do List By Vue.</p>
                </div>
                <div class="col l4 offset-l2 s12">
                    <h5 class="white-text">Links</h5>
                    <ul>
                        <li>
                            <a class="grey-text text-lighten-3" href="https://github.com/SeojinSeojin/vue-js_practice">
                                <img width="20" height="20" src="https://cdn.icon-icons.com/icons2/2368/PNG/512/github_logo_icon_143772.png"/>
                            </a>
                        </li>
                        <li>
                            <a class="grey-text text-lighten-3" href="https://velog.io/@1106laura">Velog</a>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
        <div class="footer-copyright">
            <div class="container">
            © 2021 Seojinseojin
            </div>
        </div>
    </footer>
</template>

<script>
export default {
  name: "Footer"
};
</script>

<style scoped>
footer {
    box-shadow:  0px -10px 50px #989898;
    background-color: #426b5588;
    backdrop-filter: blur(5px);
}
</style>
