
// BLOGTOC
// ------------------------------------------------ ---
يخلق BlogToc جدول محتويات قابل للنقر عليه
// مدون مدونات.
/ / يستخدم خلاصة نشر JSON ، وإنشاء ToC منه.
/ / يمكن تصنيف ToC حسب العنوان أو التاريخ ، كلاهما
// تصاعدي وتنازلي ، ويمكن تصفيته
// ضع الكلمة المناسبة.
// ------------------------------------------------ ---
// الكاتب: بيتا الجميلة
// رابط: http://beautifulbeta.blogspot.com
// الإصدار 2
// التاريخ: 2007-04-12
// ------------------------------------------------ ---
// التعديل من قبل Aneesh 
// www.bloggerplugins.org
// تعريب مدونة كن داعيا للخير 
// http://www.condaianllkhir.com/
// التاريخ: 02-08-2011
// المصفوفات العالمية

   var postTitle = new Array ()؛ // مجموعة من العناوين
   var postUrl = new Array ()؛ // مجموعة من posturls
   var postDate = new Array ()؛ // مجموعة من نشر نشر التواريخ
   var postSum = new Array ()؛ // مجموعة من ملخصات الوظائف
   var postLabels = new Array ()؛ // مجموعة من ملصقات المشاركة

// المتغيرات العالمية
   var sortBy = "datenewest"؛ // القيمة الافتراضية لفرز ToC
   var tocLoaded = false؛ / صحيح إذا تمت قراءة الخلاصة ويمكن عرض ToC
   فار numChars = 250 ؛ // عدد الأحرف في ملخص النشر
   var postFilter = ''؛ // قيمة التصفية الافتراضية
   var tocdiv = document.getElementById ("bp_toc")؛ // الحاوية toc
   var totalEntires = 0؛ // إدخالات أمسك حتى الآن
   var totalPosts = 0؛ // إجمالي عدد المشاركات في المدونة.

// وظيفة رد الاتصال الرئيسية

وظيفة loadtoc (json) {

   وظيفة getPostData () {
   / / هذه الوظائف تقرأ جميع بيانات النشر من ملف json-feed وتخزينها في صفائف
      إذا ("الدخول" في json.feed) {
         var numEntries = json.feed.entry.length؛
         totalEntires = totalEntires + numEntries؛
         totalPosts = json.feed.openSearch $ totalResults. $ ر
         إذا (totalPosts> totalEntires)
         {
         var nextjsoncall = document.createElement ('script')؛
         nextjsoncall.type = 'text / javascript'؛
         startindex = totalEntires + 1؛
         nextjsoncall.setAttribute ("src"، "/ feeds / posts / summary؟ start-index =" + startindex + "& max-results = 500 & alt = json-in-script & callback = loadtoc")؛
         tocdiv.appendChild (nextjsoncall)؛
         }
      // حلقة رئيسية تحصل على جميع الإدخالات من الخلاصة
         من أجل (var i = 0 ؛ i <numEntries؛ i ++) {
         // الحصول على الإدخال من الخلاصة
            var entry = json.feed.entry [i]؛

         // الحصول على عنوان البريد من الإدخال
            var posttitle = entry.title. $ t؛

         // الحصول على تاريخ النشر من الإدخال
            var postdate = entry.published. $ t.substring (0،10)؛

         // الحصول على عنوان URL المنشور من الإدخال
            فار بوستورل
            لـ (var k = 0؛ k <entry.link.length؛ k ++) {
               if (entry.link [k] .rel == 'alternate') {
               posturl = entry.link [k] .href؛
               استراحة؛
               }
            }

         // الحصول على محتويات المنشور من الإدخال
         / / قم بتجميع جميع أحرف html ، وقم بتصغيرها إلى ملخص
            إذا ("محتوى" في الإدخال) {
               var postcontent = entry.content. $ t؛}
            آخر
               إذا ("الملخص" في الإدخال) {
                  var postcontent = entry.summary. $ t؛}
               var varcontent = ""؛
         // تجريد جميع علامات HTML
            var re = / <\ S [^>] *> / g؛ 
            postcontent = postcontent.replace (re، "")؛
         / قم بتقليل محتوى postcontent إلى أحرف numchar ، ثم قم بقصه في الكلمة الأخيرة بالكامل
            if (postcontent.length> numChars) {
               postcontent = postcontent.substring (0، numChars)؛
               var quoteEnd = postcontent.lastIndexOf ("")؛
               postcontent = postcontent.substring (0 ، quoteEnd) + '...'؛
            }

         // الحصول على ملصقات المنشورات من الإدخال
            var pll = ''؛
            إذا ("الفئة" في الإدخال) {
               لـ (var k = 0؛ k <entry.category.length؛ k ++) {
                  pll + = '<a href = "javascript: filterPosts (\' '+ entry.category [k] .term +' \ ')؛" title = "انقر هنا لتحديد كل المنشورات ذات التصنيف \ '' + entry.category [k] .term + '\'" '' + entry.category [k] .term + '</a>،'؛
               }
            var l = pll.lastIndexOf ('،')؛
            if (l! = -1) {pll = pll.substring (0، l)؛ }
            }

         / / أضف بيانات النشر إلى المصفوفات
            postTitle.push (posttitle)؛
            postDate.push (أخر التاريخ)؛
            postUrl.push (posturl)؛
            postSum.push (postcontent)؛
            postLabels.push (PLL)؛
         }
      }
      if (totalEntires == totalPosts) {tocLoaded = true؛ showToc ()؛}
   } // نهاية getPostData

// بداية الجسم وظيفة showtoc
// الحصول على عدد الإدخالات الموجودة في الخلاصة
// numEntries = json.feed.entry.length؛

/ / احصل على بيانات النشر من الخلاصة
   getPostData ()؛

/ / فرز المصفوفات
   sortPosts (sortBy)؛
   tocLoaded = صواب ؛
}



// تصفية وفرز الوظائف


وظيفة مرشحالمنشورات (مرشح) {
/ / هذه الوظيفة تغير المرشح
// ويعرض قائمة المنشورات التي تمت تصفيتها
  // document.getElementById ("bp_toc"). scrollTop = document.getElementById ("bp_toc"). offsetTop ؛؛
   postFilter = مرشح ؛
   displayToc (postFilter)؛
} // نهاية filterPosts

وظيفة allPosts () {
/ / هذه الوظيفة تعيد ضبط الفلتر
// ويعرض جميع المشاركات

   postFilter = ''؛
   displayToc (postFilter)؛
} // end allPosts

وظيفة sortPosts (sortBy) {
/ / هذه الوظيفة هي روتين فقاعي بسيط
// الذي يفرز المشاركات

   وظيفة مقايضة (س ، ص) {
   // مبادلة 2-إدخالات ToC عن طريق تبديل جميع عناصر الصفيف
      var temp = postTitle [x]؛
      postTitle [x] = postTitle [y]؛
      postTitle [y] = temp؛
      var temp = postDate [x]؛
      postDate [x] = postDate [y]؛
      postDate [y] = temp؛
      var temp = postUrl [x]؛
      postUrl [x] = postUrl [y]؛
      postUrl [y] = temp؛
      var temp = postSum [x]؛
      postSum [x] = postSum [y]؛
      postSum [y] = temp؛
      var temp = postLabels [x]؛
      postLabels [x] = postLabels [y]؛
      postLabels [y] = temp؛
   } // end swapPosts

   لـ (var i = 0؛ i <postTitle.length-1؛ i ++) {
      لـ (var j = i + 1؛ j <postTitle.length؛ j ++) {
         if (sortBy == "titleasc") {if (postTitle [i]> postTitle [j]) {swapPosts (i، j)؛ }}
         if (sortBy == "titledesc") {if (postTitle [i] <postTitle [j]) {swapPosts (i، j)؛ }}
         if (sortBy == "dateoldest") {if (postDate [i]> postDate [j]) {swapPosts (i، j)؛ }}
         if (sortBy == "datenewest") {if (postDate [i] <postDate [j]) {swapPosts (i، j)؛ }}
      }
   }
} // end sortPosts

// عرض toc

وظيفة عرضتوك (فلتر) {
/ / تقوم هذه الوظيفة بإنشاء جدول مكون من ثلاثة أعمدة وإضافته إلى الشاشة
   var numDisplayed = 0؛
   var tocTable = ''؛
   var tocHead1 = 'الفصول'؛
   var tocTool1 = 'انقر للتصنيف حسب العنوان' ؛
   var tocHead2 = 'التاريخ' ؛
   var tocTool2 = 'انقر للتصنيف حسب التاريخ' ؛
   var tocHead3 = 'الأقسام'؛
   var tocTool3 = ''؛
   if (sortBy == "titleasc") { 
      tocTool1 + = '(تنازلي)' ؛
      tocTool2 + = '(الأحدث أولاً)' ؛
   }
   if (sortBy == "titledesc") { 
      tocTool1 + = '(تصاعدي)' ؛
      tocTool2 + = '(الأحدث أولاً)' ؛
   }
   إذا (sortBy == "dateoldest") { 
      tocTool1 + = '(تصاعدي)' ؛
      tocTool2 + = '(الأحدث أولاً)' ؛
   }
   if (sortBy == "datenewest") { 
      tocTool1 + = '(تصاعدي)' ؛
      tocTool2 + = '(الأقدم أولاً)' ؛
   }
   if (postFilter! = '') {
      tocTool3 = 'انقر لإظهار جميع الفصول' ؛
   }
   tocTable + = '<table>' ؛
   tocTable + = '<tr>'؛
   tocTable + = '<td class = "toc-header-col1">'؛
   tocTable + = '<a href = "javascript: toggleTitleSort ()؛" title = "'+ tocTool1 +'"> '+ tocHead1 +' </a> '؛
   tocTable + = '</td>'؛
   tocTable + = '<td class = "toc-header-col2">'؛
   tocTable + = '<a href = "javascript: toggleDateSort ()؛" title = "'+ tocTool2 +'"> '+ + tocHead2 +' </a> '؛
   tocTable + = '</td>'؛
   tocTable + = '<td class = "toc-header-col3">'؛
   tocTable + = '<a href = "javascript: allPosts ()؛" title = "'+ tocTool3 +'"> '+ tocHead3 +' </a> '؛
   tocTable + = '</td>'؛
   tocTable + = '</tr>'؛
   لـ (var i = 0 ؛ أنا <postTitle.length؛ i ++) {
      if (filter == '') {
         tocTable + = '<tr> <td class = "toc-entry-col1"> <a href="' + postUrl Budapi 1800 +'" title="' + postSum Budapi الصحفيين +'">' + postTitle [ i] + '</a> </td> <td class = "toc-entry-col2">' + postDate [i] + '</td> <td class = "toc-entry-col3">' + postLabels [i] + '</td> </tr>'؛
         numDisplayed ++؛
      } آخر {
          z = postLabels [i] .lastIndexOf (filter)؛
          إذا (z! = -1) {
             tocTable + = '<tr> <td class = "toc-entry-col1"> <a href="' + postUrl Budapi 1800 +'" title="' + postSum Budapi الصحفيين +'">' + postTitle [ i] + '</a> </td> <td class = "toc-entry-col2">' + postDate [i] + '</td> <td class = "toc-entry-col3">' + postLabels [i] + '</td> </tr>'؛
             numDisplayed ++؛
          }
        }
   }
   tocTable + = '</table>'؛
   إذا (numDisplayed == postTitle.length) {
      var tocNote = '<span class = "toc-note"> عدد الفصول' + postTitle.length + 'فصل <br/> </span>'؛ }
   آخر
      var tocNote = '<span class = "toc-note"> عدد الصفحات' + numDisplayed + 'الخاصة بقسم \' '؛
      tocNote + = postFilter + '\' *** '+ postTitle.length +' العدد الكلى للموضوعات <br/> </span> '؛
   }
   tocdiv.innerHTML = tocNote + tocTable؛
} // نهاية displayToc

وظيفة toggleTitleSort () {
   if (sortBy == "titleasc") {sortBy = "titledesc"؛ }
   else {sortBy = "titleasc"؛ }
   sortPosts (sortBy)؛
   displayToc (postFilter)؛
} // end toggleTitleSort

وظيفة toggleDateSort () {
   if (sortBy == "datenewest") {sortBy = "dateoldest"؛ }
   else {sortBy = "datenewest"؛ }
   sortPosts (sortBy)؛
   displayToc (postFilter)؛
} // end toggleTitleSort


وظيفة showToc () {
  if (tocLoaded) { 
     displayToc (postFilter)؛
     var toclink = document.getElementById ("toclink")؛
   
  }
  else {alert ("Just wait ... TOC يتم تحميل")؛ }
}
"<div id = \" toc-loading \ "> جارٍ تحميل المحتوى ، يرجى الانتظار ... <br /> <img align = \" middle \ "src = \" http://2.bp.blogspot.com/ -WK0-4ILTaL8 / T0NjToWRWlI / AAAAAAAABmI / U5p3cqo9lOU / s1600 / download.gif \ "/> </div>"

دالة hideToc () {
  var tocdiv = document.getElementById ("toc")؛
  tocdiv.innerHTML = ''؛
  var toclink = document.getElementById ("toclink")؛
  toclink.innerHTML = '<a href="#" onclick="scroll(0،0)؛ showToc()؛ Effect.toggle('+"'toc-result'،'blind')؛"+'"> » عرض جدول المحتويات </a> <img src = "http://chenkaie.blog.googlepages.com/new_1.gif" /> '؛
}
"<div id = \" toc-loading \ "> جارٍ تحميل المحتوى ، يرجى الانتظار ... <br /> <img align = \" middle \ "src = \" http://2.bp.blogspot.com/ -WK0-4ILTaL8 / T0NjToWRWlI / AAAAAAAABABI / U5p3cqo9lOU / s1600 / download.gif \ "/> </div>"؛
