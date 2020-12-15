<template>
     <table>
            <thead>
                <th v-for="(column,index) in columns" v-bind:key="index">
                    <a href="#" v-on:click="sort(column.shortcode)">{{column.label}}
                    </a>
                </th>
            </thead>
            <tbody>
                <tr v-for="(cat,index) in sortedCats" v-bind:key="index">
                    <td>{{cat.title}}</td>
                    <td>{{reversedMessage(cat)}}</td>
                    <td>{{cat.published}}</td>
                    <td>{{cat.price}}</td>
                </tr>

            </tbody>
        </table>
</template>

<script>
export default {
    name: 'listCat',
    data(){
        return {
                currentSort: '',
                currentSortDir: '',
                columns: [{
                        label: 'title',
                        shortcode: 'title'
                    },
                    {
                        label: 'authors',
                        shortcode: 'authors'
                    },
                    {
                        label: 'published',
                        shortcode: 'published'
                    },
                    {
                        label: 'price',
                        shortcode: 'price'
                    }
                ],
                cats: [{
                        "img": "2862_OS.jpg",
                        "title": "Drupal 7",
                        "authors": "MERCER DAVID",
                        "published": "September 2010",
                        "price": 44.99,
                        "publishedYM": "2010-09",
                        "name": ""
                    },
                    {
                        "img": "3685EN_Amazon%20SimpleDB_LITE_0.jpg",
                        "title": "Amazon SimpleDB: LITE",
                        "authors": "CHAGANTI PRABHAKAR HELMS RICH",
                        "published": "May 2011",
                        "price": 9.99,
                        "publishedYM": "2011-05",
                        "name": ""
                    },
                    {
                        "img": "1847194141.jpg",
                        "title": "Object-Oriented JavaScript",
                        "authors": "STEFANOV STOYAN",
                        "published": "July 2008",
                        "price": 39.99,
                        "publishedYM": "2008-07"
                    },
                    {
                        "img": "0042_MockupCover_0.jpg",
                        "title": "jQuery 1.4 Reference Guide",
                        "authors": "SWEDBERG KARL CHAFFER JONATHAN",
                        "published": "January 2010",
                        "price": 39.99,
                        "publishedYM": "2010-01",
                        "name": ""
                    },
                    {
                        "img": "0386OT_Cocoa%20and%20OBjective-C%20Cookbookcov.jpg",
                        "title": "Cocoa and Objective-C Cookbook",
                        "authors": "HAWKINS JEFF",
                        "published": "May 2011",
                        "price": 39.99,
                        "publishedYM": "2011-05",
                        "name": ""
                    },
                    {
                        "img": "4668_Python%20Testing%20Cookbook.jpg",
                        "title": "Python Testing Cookbook",
                        "authors": "TURNQUIST GREG L.",
                        "published": "May 2011",
                        "price": 44.99,
                        "publishedYM": "2011-05",
                        "name": ""
                    },
                    {
                        "img": "3760OS_Linux%20Shell%20Scripting%20Cookbook.jpg",
                        "title": "Linux Shell Scripting Cookbook",
                        "authors": "LAKSHMAN SARATH",
                        "published": "January 2011",
                        "price": 44.99,
                        "publishedYM": "2011-01",
                        "name": ""
                    },
                    {
                        "img": "4965OS_Nginx%201%20Web%20Server%20Implementation%20Cookbook.jpg",
                        "title": "Nginx 1 Web Server Implementation Cookbook",
                        "authors": "SARKAR DIPANKAR",
                        "published": "May 2011",
                        "price": 39.99,
                        "publishedYM": "2011-05",
                        "name": ""
                    },
                    {
                        "img": "1048OT_HTML5%20Multimedia%20Development%20Cookbookcov.jpg",
                        "title": "HTML5 Multimedia Development Cookbookcov.jpg",
                        "authors": "CRUSE DALE JORDAN LEE",
                        "published": "May 2011",
                        "price": 39.99,
                        "publishedYM": "2011-05",
                        "name": ""
                    },
                    {
                        "img": "0942OT_Core%20Data%20Essentials_0.jpg",
                        "title": "Core Data Essentials.jpg",
                        "authors": "HARWANI B.M.",
                        "published": "April 2011",
                        "price": 44.99,
                        "publishedYM": "2011-04",
                        "name": ""
                    },
                    {
                        "img": "3524OS_WordPress%203%20Plugin%20Development%20Essentials_0.jpg",
                        "title": "WordPress 3 Plugin Development Essentials",
                        "authors": "BONDARI BRIAN GRIFFITHS EVERETT",
                        "published": "March 2011",
                        "price": 39.99,
                        "publishedYM": "2011-03",
                        "name": ""
                    },
                    {
                        "img": "9867_Latex%20cov.jpg",
                        "title": "LaTeX Beginner's Guide",
                        "authors": "KOTTWITZ STEFAN",
                        "published": "March 2011",
                        "price": 44.99,
                        "publishedYM": "2011-03",
                        "name": ""
                    },
                    {
                        "img": "2923OS_Panda3D%20game%20developer%E2%80%99s%20cookbook.jpg",
                        "title": "Panda3D 1.7 Game Developer's Cookbook",
                        "authors": "LANG CHRISTOPH",
                        "published": "March 2011",
                        "price": 44.99,
                        "publishedYM": "2011-03",
                        "name": ""
                    },
                    {
                        "img": "1926_Cake%20PHP%201.3cov.jpg",
                        "title": "CakePHP 1.3 Application Development Cookbook",
                        "authors": "IGLESIAS MARIANO",
                        "published": "March 2011",
                        "price": 39.99,
                        "publishedYM": "2011-03",
                        "name": ""
                    },
                    {
                        "img": "4804os_mockupcover_ex.jpg",
                        "title": "Magento 1.4 Themes Design",
                        "authors": "CARTER RICHARD",
                        "published": "January 2011",
                        "price": 39.99,
                        "publishedYM": "2011-01",
                        "name": ""
                    },
                    {
                        "img": "0349OS_MockupCover_0.jpg",
                        "title": "Django JavaScript Integration: AJAX and jQuery",
                        "authors": "HAYWARD JONATHAN",
                        "published": "January 2011",
                        "price": 44.99,
                        "publishedYM": "2011-01",
                        "name": ""
                    },
                    {
                        "img": "1445OS_MockupCover_Magento_1.4_Development_Cookbook_cb.jpg",
                        "title": "Magento 1.4 Development Cookbook",
                        "authors": "FERDOUS NURUL",
                        "published": "December 2010",
                        "price": 44.99,
                        "publishedYM": "2010-12",
                        "name": ""
                    }
                ]
        }
    },
    methods: {
        sort(s){
            console.log(this.currentSort)
            if (s === this.currentSort) {
                this.currentSortDir = this.currentSortDir === 'asc' ? 'desc' : 'asc';
            }
            this.currentSort = s;
        },
        reversedMessage (cat){
             var arr = cat.authors.split(" ");
                    var newArr = [];
                    var i = 0;
                    var k = 0;
                    arr.forEach(element => {
                        element = element.toLowerCase()
                        if (element.charAt(1) == ".") {
                            element = element.toUpperCase()
                        } else {
                            element = element.charAt(0).toUpperCase() + element.slice(1)
                        }
                        newArr[i] = element
                        i++
                    });
                    if (i <= 2) {
                        return newArr.join(" ").split(' ').reverse().join(' ')
                    } else if (i == 3) {
                        return newArr[1] + " " + newArr[2] + " " + newArr[0];
                    } else {
                        // console.log(newArr)
                        var tmp = [];
                        for (var j = 0; j < newArr.length; j++) {
                            if (j % 2 != 0) {
                                tmp[k] = newArr[j] + " " + newArr[j - 1] + ","
                                // console.log(str)
                                k++
                            }
                        }
                        tmp = tmp.join(" ").slice(0, -1)
                        // console.log(tmp)
                        return tmp
                    }
        }
    },
    computed: {
                sortedCats: function () {
                    return this.cats.sort((a, b) => {
                        let modifier = 1;
                        if (this.currentSortDir === 'desc') modifier = -1;
                        if (a[this.currentSort] < b[this.currentSort]) return -1 * modifier;
                        if (a[this.currentSort] > b[this.currentSort]) return 1 * modifier;
                        return 0;
                    });
                },

            },
}
</script>