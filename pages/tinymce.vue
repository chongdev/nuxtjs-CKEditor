<template>
    <div class="container my-5 mx-auto max-width[600px]">
        <editor :api-key="TINYMCE_TOKEN" :init="editorConfig" v-model="editorInput" />

        <div class="mt-3">
            <h2>Preview</h2>
            <div class="editor-preview" v-html="editorInput"></div>
        </div>
    </div>
</template>

<script>
import Editor from '@tinymce/tinymce-vue'
const TINYMCE_TOKEN = process.env.TINYMCE_TOKEN;

export default {
    components: {
        'editor': Editor
    },

    data() {
        return {
            TINYMCE_TOKEN,
            editorConfig: {
                height: 500,
                images_upload_url: process.env.MEDIA_UPLOAD_URL,
                images_upload_credentials: true,
                relative_urls: false,
                remove_script_host: false,
                convert_urls: true,

                // extended_valid_elements: "p[class],figure[class],figcaption",
                // valid_children: "+p[figure]",

                menubar: false,
                autoresize_bottom_margin: 50,
                // autoresize_on_init: false,
                autoresize_overflow_padding: 24,
                plugins: [
                    // 'autoresize',
                    'underline', 'strikethrough', 'blockquote',
                    'advlist autolink lists link image charmap print preview anchor',
                    'searchreplace visualblocks code fullscreen',
                    'code, image, media, lists, table, link',
                    'insertdatetime media table paste code help wordcount'
                ],
                toolbar: [
                    'undo redo | formatselect | bold italic strikethrough underline blockquote | link image media | alignleft aligncenter alignright alignjustify | numlist bullist outdent indent | removeformat | code'
                ],
                invalid_elements: 'strong,b,em,i',
                valid_styles: 'text-align',
                branding: false,

                content_css: process.env.TINYMCE_STYLE_URL,
                block_formats: 'Paragraph=p;Header 1=h1;Header 2=h2;Header 3=h3',
                fontsize_formats: '8pt 10pt 12pt 14pt 18pt 24pt 36pt',
            },
            editorInput: `<h2 class="pagebody-header">วันดีเดย์ของ MLS ปี 2023</h2>
<div class="pagebody-copy">ในวันสุดท้ายของการแข่งขันในวันที่ 21 ตุลาคม ทุกทีมจะต้องพบกับคู่แข่งในสายเดียวกันในการต่อสู้เพื่อนัดชิงชนะเลิศและการจัดอันดับ โดยเวลาเริ่มต้นของวันดีเดย์ของ MLS จะมีการประกาศในภายหลัง</div>
<div class="pagebody-copy">รายละเอียดเกี่ยวกับนัดชิงชนะเลิศ Audi 2023 MLS Cup จะประกาศในภายหลัง</div>
<h2 class="pagebody-header">การจัดตำแหน่งสายของ MLS</h2>
<div class="pagebody-copy">ด้วยการเพิ่ม St. Louis CITY SC เข้าไปในสายตะวันตก ทำให้ Nashville SC จะกลับเข้าไปร่วมกับสายตะวันออกอีกครั้ง</div>
<h2 class="pagebody-header">โครงสร้างตารางการแข่งขันของ MLS</h2>
<blockquote>ทีมสายตะวันออก 15 ทีมจะเล่นดังนี้</blockquote>
<ul>
<li>สองนัดกับคู่แข่งขันแต่ละทีมในสายเดียวกัน (28 นัด)</li>
<li>หนึ่งนัดกับคู่แข่งขันจากคนละสาย 6 ทีมไม่ซ้ำกัน (6 นัด)</li>
</ul>

<div class="pagebody-copy">ทีมสายตะวันตก 14 ทีม จะเล่นดังนี้
<ul>
<li>สองนัดกับคู่แข่งขันแต่ละทีมในสายเดียวกัน (26 นัด)</li>
<li>หนึ่งนัดเพิ่มเติมกับทีมคู่แข่งขันในสายเดียวกัน 1 หรือ 2 ทีม (1-2 นัด)</li>
<li>หนึ่งนัดกับทีมคู่แข่งขันจากต่างสาย 6-7 ทีม (6-7 นัด)</li>
</ul>
</div>`,
            editorValue: ``
        }
    },
}
</script>