<template>
    <div>
        <ul class="links" :class="{shown: isShown}">
            <li @click="link1">Hello world</li>
            <li @click="link2">Hello world</li>
            <li @click="link3">Hello world</li>
            <li @click="link4">Hello world</li>
        </ul>
        <nav>
            <div>
                <p @click="clicked" :class="{active: isActive}" class="noselect">+</p>
            </div>
        </nav>
    </div>
</template>

<script>
export default {
    data() {
        return {
        isActive: false,
        isShown: false,
        }
    },
    methods: {
        clicked() {
            this.isActive = !this.isActive;
            this.isShown = !this.isShown;
            this.$emit('isShowingNav', this.isActive);
        },
        link1() {
            this.isShown = false;
            this.isActive = false;
            this.$emit('isShowingNav', this.isActive);
            this.$emit('showingPage1')
        },
        link2() {
            this.isShown = false;
            this.isActive = false;
            this.$emit('isShowingNav', this.isActive);
            this.$emit('showingPage2')
        },
        link3() {
            this.isShown = false;
            this.isActive = false;
            this.$emit('isShowingNav', this.isActive);
            this.$emit('showingPage3')
        },
        link4() {
            this.isShown = false;
            this.isActive = false;
            this.$emit('isShowingNav', this.isActive);
            this.$emit('showingPage4')
        },
    },
}
</script>

<style lang="scss" scoped>
    nav {
        z-index: 100;
        background: skyblue;
        position: fixed;
        top: 0px;
        left: 0px;
        width: 100vw;
        padding: none;
        div {
            padding: 0 1rem;
            margin: 0;
            display: flex;
            justify-content: flex-end;
                p {
                    margin: 0;
                transition: transform 200ms ease-in;
                font-size: 300%;
                position: relative;
                cursor: pointer;
                }
            .active {
                transform: rotate(45deg);
            }
        }
    }
    .links {
        background: lightblue;
        list-style-type: none;
        margin: 17px 0;
        padding: 0;
        position: absolute;
        left: 0;
        top: 55px;
        width: 100vw;
        z-index: 100;
        transition: transform 500ms ease;
        transform-origin: top;
        transform: scaleY(0);
        li {
            padding: 1rem 0;
            cursor: pointer;
            &:hover {
                background: skyblue;
            }
        }
    }
    .shown {
        transform: scaleY(1);
    }
    .noselect {
        -webkit-touch-callout: none; /* iOS Safari */
            -webkit-user-select: none; /* Safari */
            -khtml-user-select: none; /* Konqueror HTML */
            -moz-user-select: none; /* Old versions of Firefox */
                -ms-user-select: none; /* Internet Explorer/Edge */
                    user-select: none; /* Non-prefixed version, currently
                                        supported by Chrome, Edge, Opera and Firefox */
    }
</style>