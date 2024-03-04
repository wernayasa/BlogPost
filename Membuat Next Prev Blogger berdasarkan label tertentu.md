Membuat Next Prev Blogger berdasarkan label tertentu
====================================================

![Membuat Next Prev Blogger berdasarkan label tertentu](https://web.archive.org/web/20220908005416im_/https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEipOaB9HJ_lCdK4qQZF6HHE4Glh0NV569XBoBQ2eMLsSxuAr9iavAge9jHFnxL6D4K9HEtrb1F_yJl02FRUgVT4RNWCmxare7t80vEdT2ImsmyTGdiYDpl6NEbG1BS-Ov6cL-qdQfHL_m0XveP0jm62nmfsD7RNDU_D4tOvVMT_i6PTHABnkdskgDJzlQ/s1600/DAYAT.ID.png)

Dayat

Project yang sebelum nya terdapat di blog sebelumnya (DAGRUEL) sekarang saya remake script menjadi lebih simple.

Cara Pasang
-----------

Pertama pasang css berikut di atas tag `]]></b:skin>`.

    #nextPrevJS{display:-moz-box;display:-ms-flexbox;display:-webkit-box;display:-webkit-flex;display:flex;justify-content:space-between;align-items:center}#nextPrevJS select{background:#333;border:1px solid #333;display:block;color:#9b9b9b;padding:5px 10px;padding-right:25px;border-radius:20px;font-size:13px}#nextPrevJS .nav-right{display:-moz-box;display:-ms-flexbox;display:-webkit-box;display:-webkit-flex;display:flex;flex-wrap:wrap;gap:10px;order:2}#nextPrevJS .nav-right a{text-decoration:none;display:block;padding:2px 15px;border-radius:20px;color:#fff;font-size:13px;text-align:center;background:#366ad3;line-height:25px}#nextPrevJS .nav-right a:hover{background-color:#1c2834;color:#77828d}

Kedua pasang script berikut di atas tag `</body>`.

    const npX={arr:new Array,
      config:{
        max:150,
        start:1,
        labelMain:"Series"
      },sort:e=>e.sort((e,t)=>e.title.localeCompare(t.title,void 0,{numeric:!0})),compile:function(){let e=this.sort(this.arr).reverse(),t=this.config,a=(window||document).location.pathname,r=$('<select onchange="this.options[this.selectedIndex].value&&window.open(this.options[this.selectedIndex].value, \'_self\')" name="npx-list"></select>'),n="",i="",l="";$.each(e,(o,s)=>{s.cat.some(e=>t.labelMain==e)?n=$(`<a rel="home" href="${s.url}">${t.home||"Home"}</a>`):(r.append($(`<option ${s.url.includes(a)?'selected="selected"':""} value="${s.url}">${s.title}</option>`)),s.url.includes(a)&&(e[o+1]&&(i=e[o+1].cat.some(e=>t.labelMain==e)?"":$(`<a rel="prev" href="${e[o+1].url}">${t.prev||"Prev"}</a>`)),e[o-1]&&(l=e[o-1].cat.some(e=>t.labelMain==e)?"":$(`<a rel="next" href="${e[o-1].url}">${t.next||"Next"}</a>`))))});let o=$('<div class="nav-right"></div>');o.html(i).append(n).append(l),$("#nextPrevJS").html(r).append(o)},jqCheck:()=>"function"==typeof jQuery,xhr:function(){const e=this,t=e.config;$.ajax({type:"get",url:`${t.site||""}/feeds/posts/summary/-/${t.cat}`,data:{alt:"json","start-index":t.start,"max-results":t.max},dataType:"jsonp",success:a=>{"entry"in a.feed?($.each(a.feed.entry,(t,a)=>{e.arr.push({title:a.title.$t,url:a.link.find(e=>"alternate"==e.rel).href,cat:a.category.map(e=>e.term)})}),a.feed.entry.length>=t.max?(e.config.start+=e.config.max,e.xhr()):e.compile()):0!=e.arr.length&&e.compile()},error:()=>{$("#nextPrevJS").html(`<p>${t.textError||"Error"}</p>`)}})},run:function(){return this.jqCheck()?0==$("#nextPrevJS").length?"element tidak ada":(this.config.cat=$("#nextPrevJS").data("label")||!1,0==this.config.cat?"Category Tidak ada":void this.xhr()):"jquery tidak ada"}};npX.run();

Ganti bagian yang di tandai dengan nama label postingan info contoh: Anime, Manga, Novel.

Catatan script di atas harus memakai jquery, jadi pastikan untuk memasang jquery di template kalian.

Terakhir memasang tag html untuk menampilkan next prev nya. Terdapat dua cara, pertama di dalam post (manual), di dalam template (otomatis). Silahkan pilih salah satu.

### Manual

Cara manual cukup tempelkan ini di setiap postingan kalian.

    <div id='nextPrevJS' data-label='Nama_Label'></div>

Bagian yang di tandai adalah nama label postingan Contoh "`One Piece`".

### Otomatis

Di dalam template kalian bisa tempelkan kode berikut diatas atau dibawah kode `<data:post.body/>`.

    <b:with value='["Chapter", "NovelChapter", "MangaChapter"]' var='checkLabel'>
      <b:if cond='data:post.labels any (i => i.name in data:checkLabel)'>
        <b:loop values='data:post.labels filter (i => i.name not in data:checkLabel)' var='l'>
          <div id='nextPrevJS' expr:data-label='data:l.name'></div>
        </b:loop>
      </b:if>
    </b:with>

Bagian yang di tandai merupakan nama label postingan Chapter. berfungsi untuk menampilkan tombol next prev di label tersebut saja.

Catatan: code di atas akan berfungsi dengan baik jika postingan tersebut hanya memiliki 2 label contoh.

*   Chapter
*   One Piece

Jadi tombol next prev akan tampil di dalam postingan berlabel "Chapter". Dan label "Chapter" akan otomatis terhapus dalam looping dan akan menyisakan satu label yaitu "One Piece" untuk membuat tag next prev nya.

Sampai sini sudah selesai silahkan di coba. Untuk versi JS nya akan di update kemudian hari.

[Demo](https://web.archive.org/web/20220908005416/https://demo-source-code.blogspot.com/2022/09/next-prev.html "Membuat Next Prev Blogger berdasarkan label tertentu")

*   [_WhatsApp_](https://web.archive.org/web/20220908005416/https://wa.me/?text=Membuat Next Prev Blogger berdasarkan label tertentu - http://www.dayat.id/2022/09/next-prev-blogger.html "WhatsApp")
*   [_Telegram_](https://web.archive.org/web/20220908005416/https://t.me/share/url?url=http://www.dayat.id/2022/09/next-prev-blogger.html&text=Membuat Next Prev Blogger berdasarkan label tertentu "Telegram")
*   [_Facebook_](https://web.archive.org/web/20220908005416/https://www.facebook.com/sharer.php?u=http://www.dayat.id/2022/09/next-prev-blogger.html "Facebook")
*   [_Twitter_](https://web.archive.org/web/20220908005416/https://twitter.com/share?url=http://www.dayat.id/2022/09/next-prev-blogger.html&text=Membuat Next Prev Blogger berdasarkan label tertentu "Twitter")
*   [_Linkedin_](https://web.archive.org/web/20220908005416/https://www.linkedin.com/sharing/share-offsite/?url=http://www.dayat.id/2022/09/next-prev-blogger.html&title=Membuat Next Prev Blogger berdasarkan label tertentu "Linkedin")
