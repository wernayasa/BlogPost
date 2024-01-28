Referensi Kode Snippet Blogger
==============================

#mainbar{width:100%}  

Berikut dokumentasi kode snippet Blogger Terbaru beserta penjelasan dan contoh penulisannya.

  

Daftar Isi Artikel

1.  [Gadget Blog V2 (Widget)](#toc-1 "Gadget Blog V2 (Widget)")  
    1.  [Date (Tanggal)](#toc-1-1 "Date (Tanggal)")
    2.  [Label (Tag)](#toc-1-2 "Label (Tag)")
2.  [Page Types (Conditional Tags)](#toc-2 "Page Types (Conditional Tags)")  
    1.  [Basic](#toc-2-1 "Basic")
    2.  [Laman Khusus](#toc-2-2 "Laman Khusus")
    3.  [URL Tertentu](#toc-2-3 "URL Tertentu")
    4.  [Ringkasan](#toc-2-4 "Ringkasan")
    5.  [Contoh Penggunaan](#toc-2-5 "Contoh Penggunaan")

  

1.  ### Gadget Blog V2 (Widget Blog Post)
    
    Penggunaan snippet di dalam tag `b:loop` postingan:
    
        <b:loop values='data:posts' var='post'>
          ...
        </b:loop>
    
    1.  #### Date
        
        Menampilkan Tanggal di Postingan
        
        `data:posts[i].date`  
        
        ##### Format penulisan Published (terpublikasi)
        
            <!-- Date (published) -->
            <time expr:datetime='data:post.date.iso8601' expr:title='data:post.date.iso8601'>
              <data:post.date/>
            </time>
        
        ###### Dengan Kustomisasi
        
            <!-- Date (published) -->
            <time expr:datetime='data:post.date.iso8601' expr:title='data:post.date.iso8601'>
              <b:eval expr='format(data:post.date, "dd/MM/YYYY")'/>
            </time>
        
        ##### Format penulisan Last Updated (terpublikasi)
        
            <!-- Date (updated) -->
            <time expr:datetime='data:post.lastUpdated.iso8601' expr:title='data:post.lastUpdated.iso8601'>
              <data:post.lastUpdated/>
            </time>
        
        ###### Dengan Kustomisasi
        
            <!-- Date (updated) -->
            <time expr:datetime='data:post.lastUpdated.iso8601' expr:title='data:post.lastUpdated.iso8601'>
              <b:eval expr='format(data:post.lastUpdated, "dd/MM/YYYY")'/>
            </time>
        
        ##### Tabel Parameter Kustomisasi
        
        Period
        
        Symbol
        
        Example output
        
        Description
        
        Tahun
        
        `YY`
        
        `17`
        
        Tahun, 2 digit
        
        `YYYY`
        
        `2017`
        
        Tahun, 4 digit
        
        Bulan
        
        `M`
        
        `1`, `11`
        
        Bulan, minimum 1 digit
        
        `MM`
        
        `01`, `11`
        
        Bulan, 2 digit
        
        `MMM`
        
        `Jan`, `Nov`
        
        Bulan, 3 karakter
        
        `MMMM`
        
        `January`, `November`
        
        Bulan, nama panjang
        
        `MMMMM`
        
        `J`, `N`
        
        Bulan, karakter pertama
        
        Pekan
        
        `w`
        
        `1`, `11`
        
        Pekan dalam Tahun, minimum 1 digit
        
        `ww`
        
        `01`, `11`
        
        Pekan dalam Tahun, 2 digit
        
        `W`
        
        `4`
        
        Pekan dalam Bulan, 1 digit
        
        Hari / Tanggal
        
        `d`
        
        `1`, `11`
        
        Tanggal dalam Bulan, minimum 1 digit
        
        `dd`
        
        `01`, `11`
        
        Tanggal dalam Bulan, 2 digit
        
        `D`
        
        `1`, `55`, `362`
        
        Tanggal dalam Tahun, minimum 1 digit
        
        `DD`
        
        `01`, `55`, `362`
        
        Tanggal dalam Tahun, minimum 2 digit
        
        `DDD`
        
        `001`, `055`, `362`
        
        Tanggal dalam Tahun, minimum 3 digit
        
        `F`
        
        `3`
        
        Hari ke-X dari Bulan. Contoh; Selasa ke-3 dari Bulan.
        
        `E`
        
        `M`, `T`
        
        Nama hari dari Pekan. 1 karakter
        
        `EE`
        
        `Mo`, `Tu`
        
        Nama hari dari Pekan. 2 karakter
        
        `EEE`
        
        `Mon`, `Tue`
        
        Nama hari dari Pekan. 3 karakter
        
        `EEEE`
        
        `Monday`, `Tuesday`
        
        Nama panjang hari dari Pekan.
        
        Waktu dalam Hari
        
        `aaaa`
        
        `AM`, `PM`
        
        Namanya mungkin berbeda tergantung regional.
        
        `bbbb`
        
        `Morning`, `Afternoon`, `Evening`
        
        `BBBB`
        
        Jam
        
        `h`
        
        `1`, `11`
        
        Jam \[1-12\], minimum 1 digit
        
        `hh`
        
        `01`, `11`
        
        Jam \[1-12\], 2 digit
        
        `H`
        
        `1`, `21`
        
        Jam \[0-23\], minimum 1 digit
        
        `HH`
        
        `01`, `21`
        
        Jam \[0-23\], 2 digit
        
        Menit
        
        `m`
        
        `1`, `59`
        
        Menit, minimum 1 digit
        
        `mm`
        
        `01`, `59`
        
        Menit, 2 digit
        
    2.  #### Labels
        
        Label yang ada pada postingan.
        
        `data:posts[i].labels`  
        **Opsi Label**  
        
        `12`: adalah jumlah maksimum Label yang dapat ditampilkan pada suatu laman.
        
        ##### Default
        
            <!-- Labels -->
            <b:if cond='data:post.labels'>
              <b:loop index='i' values='data:post.labels' var='label'>
                <a expr:href='params(data:label.url, { max-results: "12" })' expr:title='data:label.name'>
                  <b:attr name='b:whitespace' value='remove'/>
                  <data:label.name/>
                </a>
              </b:loop>
            </b:if>
        
        ###### Default dengan Fallback
        
            <!-- Labels -->
            <b:if cond='data:post.labels'>
              <b:loop index='i' values='data:post.labels' var='label'>
                <a expr:href='params(data:label.url, { max-results: "12" })' expr:title='data:label.name'>
                  <b:attr name='b:whitespace' value='remove'/>
                  <data:label.name/>
                </a>
              </b:loop>
            <b:else/><!-- fallback -->
              <span>Unlabelled</span>
            </b:if>
        
        ##### Pembatas Koma
        
            <!-- Labels -->
            <b:if cond='data:post.labels'>
              <b:loop index='i' values='data:post.labels' var='label'>
                <a expr:href='params(data:label.url, { max-results: "12" })' expr:title='data:label.name'>
                  <b:attr name='b:whitespace' value='remove'/>
                  <data:label.name/>
                </a><b:if cond='data:i != (data:post.labels.size - 1)'>,</b:if>
              </b:loop>
            </b:if>
        
        ###### Pembatas Koma dengan Fallback
        
            <!-- Labels -->
            <b:if cond='data:post.labels'>
              <b:loop index='i' values='data:post.labels' var='label'>
                <a expr:href='params(data:label.url, { max-results: "12" })' expr:title='data:label.name'>
                  <b:attr name='b:whitespace' value='remove'/>
                  <data:label.name/>
                </a><b:if cond='data:i != (data:post.labels.size - 1)'>,</b:if>
              </b:loop>
            <b:else/><!-- fallback -->
              <span>Unlabelled</span>
            </b:if>
        
2.  ### Page Types (Conditional Tags)
    
    Tag kondisional pada berbagai macam tipe laman, yang memungkinkan untuk menentukan bagian dari kode template pada suatu tipe laman yang spesifik atau URL tertentu.
    
    1.  #### Basic
        
        ###### Homepage
        
            <b:if cond='data:view.isHomepage'>
              <!-- https://example.blogspot.com -->
            </b:if>
        
        ###### Single Page
        
            <b:if cond='data:view.isPost'>
              <!-- https://example.blogspot.com/<year>/<month>/<permalink>.html -->
            </b:if>
        
        ###### Static Page
        
            <b:if cond='data:view.isPage'>
              <!-- https://example.blogspot.com/p/<permalink>.html -->
            </b:if>
        
        ###### Search (Label) Page
        
            <b:if cond='data:view.search.label'>
              <!-- 1. https://example.blogspot.com/search/label/<label-name> -->
              <!-- 2. https://example.blogspot.com/search?label=<label-name> -->
            </b:if>
        
        ###### Search (Query) Page
        
            <b:if cond='data:view.search.query'>
              <!-- https://example.blogspot.com/search?q=<query> -->
            </b:if>
        
        ###### Search (Default) Page
        
            <b:if cond='data:view.search and !data:view.search.label and !data:view.search.query'>
              <!-- https://example.blogspot.com/search -->
            </b:if>
        
        ###### Archive Page
        
            <b:if cond='data:view.isArchive'>
              <!-- 1. https://example.blogspot.com/<year> -->
              <!-- 2. https://example.blogspot.com/<year>/<month> -->
              <!-- 3. https://example.blogspot.com/<year>_<month>_<day>_archive.html -->
            </b:if>
        
        ###### Error Page
        
            <b:if cond='data:view.isError'>
              <!-- https://example.blogspot.com/<404> -->
            </b:if>
        
    2.  #### Laman Khusus
        
        ###### Layout Mode
        
            <b:if cond='data:view.isLayoutMode'>
              <!-- https://www.blogger.com/blogger.g?blogID=<blogID>#pageelements -->
            </b:if>
        
        ###### Preview Page
        
            <b:if cond='data:view.isPreview'>
              <!-- Preview page -->
            </b:if>
        
    3.  #### URL Tertentu
        
        ###### Single Page Tertentu
        
            <b:if cond='data:view.url == "https://example.blogspot.com/1945/08/wow.html"'>
              <!-- https://example.blogspot.com/1945/08/wow.html -->
            </b:if>
        
        ###### Static Page Tertentu
        
            <b:if cond='data:view.url == "https://example.blogspot.com/p/wow.html"'>
              <!-- https://example.blogspot.com/p/wow.html -->
            </b:if>
        
        ###### Search (Label) Page Tertentu
        
            <b:if cond='data:view.search.label == "WOW"'>
              <!-- 1. https://example.blogspot.com/search/label/WOW -->
              <!-- 2. https://example.blogspot.com/search?label=WOW -->
            </b:if>
        
        ###### Search (Query) Page Tertentu
        
            <b:if cond='data:view.search.query == "wow"'>
              <!-- https://example.blogspot.com/search?q=wow -->
            </b:if>
        
    4.  #### Ringkasan
        
        Expression
        
        Tipe Data
        
        Keterangan
        
        `data:view.archive.day`
        
        number
        
        Day of the current archive page. e.g. 17.
        
        `data:view.archive.month`
        
        number
        
        The month of the current archive page. e.g. 8
        
        `data:view.archive.year`
        
        number
        
        Year of the current archive page. e.g. 1945
        
        `data:view.description`
        
        string
        
        Description of the current pageview.
        
        `data:view.featuredImage`
        
        image
        
        Featured image for the current page or post.
        
        `data:view.isArchive`
        
        boolean
        
        Indicating Archive feed.
        
        `data:view.isError`
        
        boolean
        
        The current view is 404 or error page.
        
        `data:view.isHomepage`
        
        boolean
        
        The current view is Homepage.
        
        `data:view.isLabelSearch`
        
        boolean
        
        The current view is the Label page.
        
        `data:view.isMultipleItems`
        
        boolean
        
        A page view is contained multiple posts, eg, Search, Label, Homepage, etc.
        
        `data:view.isMobile`
        
        boolean
        
        A pageview has parameter m=1.
        
        `data:view.isPage`
        
        boolean
        
        is Showing a Blog Static Page.
        
        `data:view.isPost`
        
        boolean
        
        is Showing a Single Post.
        
        `data:view.isPreview`
        
        boolean
        
        In preview mode.
        
        `data:view.isSearch`
        
        boolean
        
        All page contain word 'search' in the URL.
        
        `data:view.isSingleItem`
        
        boolean
        
        is a Single item, wether is the single post or static page.
        
        `data:view.pageId`
        
        number
        
        The id of the static page.
        
        `data:view.postId`
        
        number
        
        The id of the post.
        
        `data:view.search.label`
        
        string
        
        Used for filtering label of the current view.
        
        `data:view.search.query`
        
        string
        
        Used for filtering search keyword.
        
        `data:view.search.resultsMessage`
        
        string
        
        The message about the search results being shown.
        
        `data:view.search.resultsMessageHtml`
        
        string
        
        A message about the result with HTML Link.
        
        `data:view.title`
        
        string
        
        Title of the current view.
        
        `data:view.url`
        
        url
        
        The URL of the current view.
        
    5.  #### Contoh Penggunaan
        
        ##### Sintaks dan Atributnya
        
            <b:if cond='EXPRESSION'>
             <!-- executed if a specified condition is true -->
            <b:elseif cond='EXPRESSION2'/>
             <!-- executed if upper condition test is false  -->
            <b:else/>
             <!-- executed if all condition is false -->
            </b:if>
        
        ##### Contoh Tag Kondisional
        
        **Dengan Blogger Data Expression**  
        
            <b:if cond='data:view.isHomepage'>
             <!-- Execute -->
            </b:if>
        
        **Dengan Data Boolean**  
        
            <b:if cond='data:blog.pageTitle'>
             <b:if cond='false'>
              <!-- Execute -->
             </b:if>
            </b:if>
        
        **Dengan Operator Komparasi**  
        
            <b:if cond='data:blog.isMobile == "true"'>
             <!-- Execute -->
            </b:if>
        
        **Dengan Operator Membership**  
        
            <b:if cond='!data:view.isMobile and data:view.isHomepage or data:view.isSearch'>
             <!-- Execute -->
            </b:if>
        
        **Dengan Operator Lambda**  
        
            <b:if cond='data:view.search.label in ["Foo", "Bar", "Baz"]'>
             <!-- span Block 1 -->
            <b:elseif cond='data:view.search.label not in ["Baz", "Qux"]'/>
             <!-- span Block 2 --> 
            <b:else/>
             
            </b:if>
        

  

* * *

  
Reference:  
\[1\] https://wrapblogger.github.io/blogger/snippets/  
\[2\] https://bloggerbook.blakbin.com/2018/11/blogger-cheatsheet-dataview.html  
\[3\] https://bloggerbook.blakbin.com/2018/11/blogger-bif-belse-and-belseif-tag.html  
\[4\] https://support.google.com/blogger/answer/47270?hl=en  
\[5\] https://bloggercode-blogconnexion.blogspot.com/  
