# tugas

## Pengenalan

Tugas `Vue-Quiz` ini merupakan sebuah web yang dibuat oleh **vue-js** dimana web ini memiliki persamaan dengan quiz-quiz web yang lainnya. Jika jawaban benar, maka nilai akan bertambah, sedangkan jika salah, maka nilai akan tetap.

## Cara Install
1. 1. Clone project di atas
2. Extract Files tersebut, lalu pindahan ke tempat yang diinginkan
3. Ketika sudah diarahkan ke file tersebut, maka buka _cmd_ lalu arahkan _cmd_ tersebut ke file yang tadi
4. Install *node_modules* dengan cara ketik: **npm install**
5. Setelah proses instalasi selesai, maka langsung ketik saja: **npm run serve**
6. Biasanya akan muncul link untuk menjalankan `project-vue` tersebut, seperti contoh di bawah ini :

```
App running at:
- Local: localhost:8081/
- Network: your.ip:8081/
```

## Code Di Dalam Aplikasi

### Array Untuk Soal
```
questions: [{
        text: "Dibawah ini yang termasuk bahasa pemrograman adalah",
        jawaban: [{
            text: 'Windows',
            choice: '0'
        }, {
            text: 'HTML',
            choice: '1'
        }, {
            text: 'Linux',
            choice: '2'
        }, {
            text: 'Edubox',
            choice: '3'
        }],
        correct: '1'
    },
    ...
```

### Pemanggilan di dalam HTML
```
<div v-for="(question, index) in quiz.questions" v-bind:key="question.id">
        <div v-show="index == questionIndex">
            <h4>{{ question.text }}</h4>
            <ol>
                <li v-for="response in question.jawaban" v-bind:key="response.id">
                    <label>
                        <input type="radio" v-bind:value="response.choice" v-bind:name="index" v-model="memilih"> {{ response.text }}
                    </label>
                </li>
            </ol>

            <button v-on:click="check(question.correct, memilih)">
                <span v-if="questionIndex == quiz.questions.length - 1">Selesai</span>
                <span v-else>Lanjut</span>
            </button>

            <h5>Score: {{ hasil }}</h5>
        </div>
    </div>

    <div v-show="questionIndex == quiz.questions.length">
        <h2>Kuis Selesai</h2>
        <p>Score: {{ hasil }} Dari {{ quiz.questions.length }}</p>
    </div>
</div>
```

### Logika Di Dalam Kodingannya
```
data: function() {
        return {
            show: true,
            questionIndex: 0,
            quiz: quiz,
            hasil: 0,
            memilih: '',
        }
    },
    methods: {
        check(correct, memilih) {
                if (correct === memilih)
                    this.hasil++;
                this.questionIndex++;
            }
    }
```

## Penjelasan Kodingan
Untuk pertama-tama, saya memasukkan semua soal di dalam satu array. Lalu, saya menggunakan *nested_array*, dimana akan ada array di dalam array. Lalu, untuk menentukan mana jawaban yang benar dan mana jawaban yang salah, saya mengambil dari index array tersebut. Untuk pemanggilannya sendiri, saya menggunakan *for_loop* atau *v-for* lalu memunculkan semua soal-soal di dalam array yang telah saya masukkan.

Setelah itu, saya memanggil method-method yang di dalamnya adalah sebuah logika. Jika jawaban yang dipilih user sesuai dengan index yang benar, nilai akan bertambah.

## Hasil Dari Kodingan
![alt text](https://github.com/mohripan/Tugas/blob/master/hasil.jpg)
