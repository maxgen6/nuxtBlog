<template>
    <article class="post">
        <header class="post-heder">
            <div class="post-title">
                <h1>Post title</h1>
                <nuxt-link to="/">
                    <i class="el-icon-back"></i>
                </nuxt-link>
            </div>
            <div class="post-info">
                <small>
                    <i class="el-icon-time"></i>
                    {{ new Date().toLocaleString()}}
                </small>
                <small>
                  <i class="el-icon-view"></i>
                  42  
                </small>
            </div>
            <div class="post-image">
                <img 
                    src="https://m.newsland.com/static/u/u/news/2019/08/c7a841c5aee94567ae26adb5d8690b00.jpg" 
                    alt="post image" 
                >
            </div>
        </header>
        <main class="post-content">
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Est esse culpa qui. Repellendus ab soluta fuga, quod accusamus asperiores illo odio adipisci magnam! Blanditiis officiis at reiciendis aperiam, sed natus?</p>  
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Est esse culpa qui. Repellendus ab soluta fuga, quod accusamus asperiores illo odio adipisci magnam! Blanditiis officiis at reiciendis aperiam, sed natus?</p>  
          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Est esse culpa qui. Repellendus ab soluta fuga, quod accusamus asperiores illo odio adipisci magnam! Blanditiis officiis at reiciendis aperiam, sed natus?</p>  
        </main>
        <footer>
            <app-comment-form 
                v-if="canAddComment"
                @created="createCommentHandler"
            />

            <div class="comments" v-if="true">
                <app-comment
                    v-for="comment in 4"
                    :key="comment"
                    :comment="comment"
                />
            </div>

            <div class="text-center" v-else>Комментариев нет</div>
        </footer>

    </article>
</template>

<script>
import AppCommentForm from '@/components/main/CommentForm'
import AppComment from '@/components/main/Comment'
export default {
    validate({params}) {
        return Boolean(params.id)
    },
    data() {
        return {
            canAddComment: true
        }
    },
    methods: {
        createCommentHandler() {
            this.canAddComment = false
        }
    },
    components: {
        AppComment,
        AppCommentForm
    }
}
</script>

<style lang="scss" scoped>
    .post {
        max-width: 600px;
        margin: 0 auto;
    }

    .post-title {
        display: flex;
        justify-content: space-between;
        margin-bottom: 1rem;
    }

    .post-info {
        display: flex;
        justify-content: space-between;
        margin-bottom: 0.5rem;
    }

    .post-image img{
        width: 100%;
        height: auto;
    }

    .post-header {
        margin-bottom: 1.5rem;
    }

    .post-content {
        margin-bottom: 2rem;
    }
</style>