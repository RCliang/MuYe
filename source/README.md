# Home

# MuYe'Blog 牧野的个人博客、面经及其他资料URL

---

<div class="home-book-list">
    <!-- java -->
    <div class="home-book-list-item">
        <a href="/MuYe/books/interview/MachineLearning/index.html" class="home-book-list-image">
            <div>
                <img src="/MuYe/static/cover/MachineLearning.png" /> 
            </div>
            <div class="home-book-list-title">
                面筋
            </div>
            <div class="home-book-list-desc">
                机器学习相关问题
            </div>
        </a>
    </div>
</div>

---

最新发表的博客文章：

<div id="home-blog-list" class="home-blog-list">文章列表</div>

<script>
    documentReady(async ()=>{
        const resp = await fetch('/MuYe/blogs/all/index.json');
        let blogs = await resp.json();
        if (blogs.length > 20) {
            blogs = blogs.slice(0, 20);
        }
        console.log(JSON.stringify(blogs));
        const items = blogs.map(blog => {
            let date = new Date(blog.date).toLocaleDateString(undefined, { year: 'numeric', month: 'long', day: 'numeric' });
            return `
<div class="home-blog-list-item">
    <div><span class="text-sm font-semibold uppercase">${date}</span></div>
    <div><a href="/MuYe${blog.uri}">${gitsite.encodeHtml(blog.title)}</a></div>
</div>`;
        });
        document.getElementById('home-blog-list').innerHTML = items.join('');
    });
</script>
