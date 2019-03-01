<template>
    <div class="mosaique_B">
        <!-- wwManager:start -->
        <wwSectionEditMenu v-bind:sectionCtrl="sectionCtrl"></wwSectionEditMenu>
        <!-- wwManager:end -->

        <wwObject class="background" v-bind:ww-object="section.data.background" ww-category="background"></wwObject>

        <div class="container section-padding">
            <div class="row">
                <div class="section-title-container col-xs-12 col-md-8 col-md-offset-2">
                    <h1 class="section-title">
                        <wwObject v-bind:ww-object="section.data.title"></wwObject>
                    </h1>
                    <div class="section-subtitle">
                        <wwObject v-bind:ww-object="section.data.subtitle"></wwObject>
                    </div>
                </div>
            </div>

            <div class="row slider-bigger-container">
                <div class="slider-container">
                    <div class="slides block" v-for="(block, index) in section.data.blocks" :key="block.uniqueId">
                        <div class="block-img-container">
                            <wwObject v-bind:ww-object="block.img"></wwObject>
                        </div>

                        <!-- wwManager:start -->
                        <div v-show="editMode" class="edit-button-top-left" @click="remove(section.data.blocks, { index })">
                            <i class="wwi wwi-delete" aria-hidden="true"></i>
                        </div>
                        <!-- wwManager:end -->
                    </div>

                    <!-- wwManager:start -->
                    <div v-if="editMode" class="block">
                        <div class="add-block">
                            <wwLayoutPlus @click="add(section.data.blocks, getNewBlock())"></wwLayoutPlus>
                        </div>
                    </div>
                    <!-- wwManager:end -->

                </div>

                <!-- SLIDER BUTTON -->
                <div class="arrow-right" style="z-index:10000">
                    <i class="wwi wwi-chevron-right"></i>
                    <div class="arrow-hover"></div>
                </div>

                <div class="arrow-left">
                    <i class="wwi wwi-chevron-left"></i>
                    <div class="arrow-hover"></div>
                </div>
                
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "mosaique_B",
    props: {
        sectionCtrl: Object
    },
    data() {
        return {}
    },
    computed: {
        section() {
            return this.sectionCtrl.get();
        },
        // wwManager:start
        editMode() {
            return this.sectionCtrl.getEditMode() == 'CONTENT'
        }
        // wwManager:end
    },
    created() {
        //Initialize section data
        this.section.data = this.section.data || {};
        this.section.data = {"isNew":false,"title":{"data":{},"font":"","link":"","size":"text-big","text":{"fr":"This is the Duo Right Section"},"zoom":-1,"align":"","class":["ww-anim-fade"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.7654089558898747},"blocks":[{"img":{"data":{},"font":"","link":null,"size":"","text":{"fr":""},"zoom":-1,"align":"","class":["ww-anim-fade-right"],"image":"https://wewebprod.s3-eu-west-1.amazonaws.com/designs/46/sections/DWOAAeJ1PaA6eGT54h4jbBCnyZOydNJS.jpg","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.1386103572748143},"text":{"data":{},"font":"","link":"","size":"text-small","text":{"fr":"Start editing by hitting the pen!"},"zoom":-1,"align":"center","class":["ww-anim-fade-top-bounce"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.7568700109770659},"title":{"data":{},"font":"","link":"","size":"text-medium","text":{"fr":"Use it to illustrate your story, products or services..."},"zoom":-1,"align":"center","class":["ww-anim-fade-top-bounce"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.7092767280205428},"button":{"data":{},"font":"","link":"http://getweweb.com","size":"","text":{"fr":"Call to action"},"zoom":-1,"align":"","class":["ww-anim-fade-top","ww-class-btn-border-small","ww-class-btn-padding-small","ww-class-font-size-xsmall","ww-class-btn-format-round-small","ww-class-btn-shadow-bottom-small","ww-anim-fade-top-bounce"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"#000000","borderColor":"#000000","backgroundColor":"#FFFFFF"},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.6103822515821822},"textImg":"Coucou !","uniqueId":1,"textStyle":{"align":"left"},"titleStyle":{"size":"text-small","align":"left"}},{"img":{"data":{},"font":"","link":null,"size":"","text":{"fr":""},"zoom":-1,"align":"","class":["ww-anim-fade-right"],"image":"https://wewebprod.s3-eu-west-1.amazonaws.com/designs/46/sections/Z5y7mMfRSSlsE2MwpjdELF1Tl0RrN6Cy.jpg","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.6180333197744869},"text":{"data":{},"font":"","link":"","size":"text-small","text":{"fr":"You can delete pictures by hitting the \"x\" on the top left corner. "},"zoom":-1,"align":"center","class":["ww-anim-fade-top-bounce"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.37987720101429656},"title":{"data":{},"font":"","link":"","size":"text-medium","text":{"fr":"You can add pictures by hitting the \"+\" below."},"zoom":-1,"align":"center","class":["ww-anim-fade-top-bounce"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.05367059587731693},"button":{"data":{},"font":"","link":"http://getweweb.com","size":"","text":{"fr":"Call to action"},"zoom":-1,"align":"","class":["ww-anim-fade-top","ww-class-btn-border-small","ww-class-btn-padding-small","ww-class-font-size-xsmall","ww-class-btn-format-round-small","ww-class-btn-shadow-bottom-small","ww-anim-fade-top-bounce"],"image":"/img/no_image_selected.png","ratio":-1,"colors":{"color":"#000000","borderColor":"#000000","backgroundColor":"#FFFFFF"},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.27197412090188355},"textImg":"Coucou !","uniqueId":2,"textStyle":{"align":"left"},"titleStyle":{"size":"text-small","align":"left"}}],"background":{"data":{},"font":"","link":null,"size":"","text":{"fr":""},"zoom":-1,"align":"","class":[],"image":"#FFFFFF","ratio":-1,"colors":{"color":"","borderColor":"","backgroundColor":""},"hidden":false,"position":{"x":0,"y":0},"uniqueId":0.18048312431083202},"titleStyle":{"size":"text-big"},"sectionTitle":"Duo right"}
        this.section.data.blocks = this.section.data.blocks || [this.getNewBlock()];

        if (!this.section.data.background) {
            this.section.data.background = wwLib.wwObject.getDefault({ type: 'ww-color' });
        }
        if (!this.section.data.title) {
            this.section.data.title = wwLib.wwObject.getDefault({ type: 'ww-text' });
        }
        if (!this.section.data.subtitle) {
            this.section.data.subtitle = wwLib.wwObject.getDefault({ type: 'ww-text' });
        }
        this.sectionCtrl.update(this.section);
    },
    mounted() {
        this.$nextTick(() => {
            const left = this.$el.querySelector('.arrow-left'),
                right = this.$el.querySelector('.arrow-right');

            const slider = this.$el.querySelector('.slider-container');
            const position = slider.offsetLeft;
            
            if (position === 0) {
                left.classList.add('hidden');
            }

            left.addEventListener('mouseover', function (event) { // start animation to the end of the slider and stops when mouse leaves
                const slider = left.parentElement.querySelector('.slider-container')
                const position = slider.getBoundingClientRect().left;

                slider.style.transition = 'transform ' + Math.abs(position * 3) + 'ms ease'
                slider.style.transform = 'translateX(0px)'
                return false;
            })
            left.addEventListener('mouseout' , function (event) { // start an animation when mouse leaves to add a smooth effect
                const slider = left.parentElement.querySelector('.slider-container')
                const position = slider.getBoundingClientRect().left;
                let targetPos = position + 100;
                targetPos = targetPos > 0 ? 0 : targetPos;

                slider.style.transition = 'transform 500ms ease'
                slider.style.transform = 'translateX(' + targetPos + 'px)'

                if (position === 0) {
                    left.classList.add('hidden');
                }
            })

            right.addEventListener('mouseover', function (event) { // start animation to the end of the slider and stops when mouse leaves
                left.classList.remove('hidden');
                const slider = right.parentElement.querySelector('.slider-container')
                const position = slider.getBoundingClientRect().left;
                const slideCount = slider.getElementsByClassName('block').length - (this.editMode ? 1 : 0);
                const slideWidth = slider.getElementsByClassName('block')[0].offsetWidth + 8; // each slides has a padding of 4 on each sides so  2*4
                const sliderWidth = slideCount * slideWidth + 4; // 4 : padding of the slides
                const windowWidth = window.innerWidth;
                const targetPos = -(sliderWidth - windowWidth);

                slider.style.transition = 'transform ' + Math.abs((targetPos - position) * 3) + 'ms ease'
                slider.style.transform = 'translateX(' + targetPos + 'px)'

                return false;
            })
            right.addEventListener('mouseout', function () { // start an animation when mouse leaves to add a smooth effect
                const slider = right.parentElement.querySelector('.slider-container')
                const position = slider.getBoundingClientRect().left;
                const targetPos = position - 100;
                const slideCount = slider.getElementsByClassName('block').length - (this.editMode ? 1 : 0);
                const slideWidth = slider.getElementsByClassName('block')[0].offsetWidth + 8; // each slides has a padding of 4 on each sides so  2*4
                const sliderWidth = slideCount * slideWidth + 4; // 4 : padding of the slides
                const windowWidth = window.innerWidth;

                targetPos = targetPos < -(sliderWidth - windowWidth) ? -(sliderWidth - windowWidth) : targetPos;

                slider.style.transition = 'transform 500ms ease'
                slider.style.transform = 'translateX(' + targetPos + 'px)'
            })
        })
    },
    methods: {
        getNewBlock() {
            return {
                img: wwLib.wwObject.getDefault({ type: 'ww-image', ratio: 50 })
            }
        },
        // wwManager:start
        add(array, elem) {
            array.push(elem);
            this.sectionCtrl.update(this.section);
        },
        remove(array, options) {
            array.splice(options.index, 1);
            this.sectionCtrl.update(this.section);
        }
        // wwManager:end
    }
};
</script>

<style lang="scss" scoped>
.mosaique_B .container {
    width: 100%;
    overflow: hidden
}

.mosaique_B .background {
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
}

.mosaique_B .block {
    margin-top: 8px;
    padding-left: 4px !important;
    padding-right: 4px !important;
    display: inline-block;
    width: 250px;
    position: relative;
}

.mosaique_B .slider-container {
    -webkit-transition: transform 0.2s linear;
    -moz-transition: transform 0.2s linear;
    -ms-transition: transform 0.2s linear;
    -o-transition: transform 0.2s linear;
    transition: transform 0.2s linear;
    white-space: nowrap;
}

.mosaique_B .arrow-right {
    position: absolute;
    height: 100%;
    width: 70px;
    top: 0;
    right: 0;
    z-index: 100;
    pointer-events: all;
    i {
        position: absolute;
        font-size: 30px;
        top: 50%;
        left: 35px;
        color: #333;
        border-radius: 50%;
        padding: 12px;
        box-shadow: 1px 1px 4px #333;
        background-color: white;
        -webkit-transform: translate(-50%, -50%);
        -moz-transform: translate(-50%, -50%);
        -ms-transform: translate(-50%, -50%);
        -o-transform: translate(-50%, -50%);
        transform: translate(-50%, -50%);
    }
}

.mosaique_B .arrow-left {
    position: absolute;
    height: 100%;
    width: 70px;
    top: 0;
    left: 0;
    z-index: 100;
    pointer-events: all;
    i {
        position: absolute;
        font-size: 30px;
        top: 50%;
        left: 35px;
        border-radius: 50%;
        padding: 12px;
        box-shadow: 1px 1px 4px #333;
        background-color: white;
        -webkit-transform: translate(-50%, -50%);
        -moz-transform: translate(-50%, -50%);
        -ms-transform: translate(-50%, -50%);
        -o-transform: translate(-50%, -50%);
        transform: translate(-50%, -50%);
    }
}

.mosaique_B .slider-bigger-container {
    position: relative;
}

.mosaique_B .arrow-hover {
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    z-index: 1;
}

.mosaique_B .arrow-left .arrow-hover {
    left: -30px;
}

.mosaique_B .arrow-right .arrow-hover {
    right: -30px;
}

.mosaique_B .block .block-img-container {
    width: 100%;
    position: relative;
}

.mosaique_B .row {
    display: -ms-flexbox;
    display: flex;
    -ms-flex-wrap: wrap;
    flex-wrap: wrap;
    margin-right: -15px;
    margin-left: -15px;
}

.mosaique_B .section-title {
    margin-bottom: 5px;
}

.mosaique_B .section-padding {
    padding: 30px 15px
}

.mosaique_B .block .add-block {
    position: relative;
    display: flex;
    justify-content: center;
}

.mosaique_B .section-title-container {
    position: relative;
    width: 100%;
    min-height: 1px;
    padding-right: 15px;
    padding-left: 15px;
    -ms-flex: 0 0 100%;
    flex: 0 0 100%;
    max-width: 100%;
}

@media (min-width: 768px) {
    .mosaique_B .section-padding {
        padding: 50px 30px
    }
}

@media (max-width: 992px) {
    .mosaique_B .slider-bigger-container {
        overflow-x: scroll;
    }
    .mosaique_B .arrow-right {
        display: none;
    }
    .mosaique_B .arrow-left {
        display: none;
    }
    .mosaique_B .block {
        width: 150px !important;
    }
}

@media (min-width: 1024px) {
    .mosaique_B .section-padding {
        padding: 75px 50px
    }
    .mosaique_B .section-title-container {
        -ms-flex: 0 0 66.666666%;
        flex: 0 0 66.666666%;
        max-width: 66.666666%;
        margin-left: 16.666666%;
    }
}

@media (max-width: 1200px) {
    .mosaique_B .block {
        width: 200px !important;
    }
}

@keyframes arrow {
    from {
        color: #bfbfbf;
    }
    to {
        color: #333;
    }
}

/* wwManager:start */
.mosaique_B .edit-button-top-left {
    position: absolute;
    left: -5px;
    top: -13px;
    width: 26px;
    height: 26px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 100%;
    text-align: center;
    font-size: 18px;
    line-height: 36px;
    cursor: pointer;
    pointer-events: all;
    z-index: 3;
    color: white;
    background-color: #E73055;
    background: linear-gradient(to right, #E73055 0%, rgb(175, 33, 61) 100%);
}

/* wwManager:end */
</style>
