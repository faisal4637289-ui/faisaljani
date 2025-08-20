import React, { useState } from "react";
import { motion } from "framer-motion";
import { Mail, Phone, MapPin, ArrowRight, Github, Globe, PlayCircle, Search } from "lucide-react";

export default function FaisalUrduSite() {
  const [search, setSearch] = useState("");
  const [category, setCategory] = useState("all");

  const movies = [
    {
      title: "مووی 1",
      category: "ایکش",
      img: "https://images.unsplash.com/photo-1598899134739-24c46f58b8c0?w=800",
      link: "https://www.youtube.com/embed/dQw4w9WgXcQ"
    },
    {
      title: "مووی 2",
      category: "کامیڈی",
      img: "https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?w=800",
      link: "https://www.youtube.com/embed/dQw4w9WgXcQ"
    },
    {
      title: "مووی 3",
      category: "ہارر",
      img: "https://images.unsplash.com/photo-1524985069026-dd778a71c7b4?w=800",
      link: "https://www.youtube.com/embed/dQw4w9WgXcQ"
    }
  ];

  const filteredMovies = movies.filter(
    (m) =>
      (category === "all" || m.category === category) &&
      m.title.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div dir="rtl" lang="ur" className="min-h-screen bg-gradient-to-b from-slate-50 via-white to-slate-100 text-slate-800">
      {/* Navbar */}
      <header className="sticky top-0 z-50 backdrop-blur bg-white/70 border-b border-slate-200">
        <nav className="mx-auto max-w-6xl px-4 sm:px-6 py-3 flex items-center justify-between">
          <a href="#home" className="font-extrabold text-xl tracking-tight">فیصل علی</a>
          <ul className="hidden sm:flex gap-6 text-sm">
            <li><a href="#about" className="hover:opacity-70">میرے بارے میں</a></li>
            <li><a href="#services" className="hover:opacity-70">خدمات</a></li>
            <li><a href="#movies" className="hover:opacity-70">موویز</a></li>
            <li><a href="#projects" className="hover:opacity-70">پراجیکٹس</a></li>
            <li><a href="#contact" className="hover:opacity-70">رابطہ</a></li>
          </ul>
          <a href="#contact" className="hidden sm:inline-flex items-center gap-2 text-sm font-semibold bg-slate-900 text-white px-4 py-2 rounded-2xl shadow hover:shadow-md">
            رابطہ کریں <ArrowRight className="w-4 h-4" />
          </a>
        </nav>
      </header>

      {/* Hero */}
      <section id="home" className="relative overflow-hidden">
        <div className="absolute inset-0 -z-10 bg-[radial-gradient(40rem_40rem_at_80%_-10%,#c7d2fe,transparent),radial-gradient(40rem_40rem_at_10%_-20%,#fecaca,transparent)]" />
        <div className="mx-auto max-w-6xl px-4 sm:px-6 py-20 sm:py-28 grid lg:grid-cols-2 gap-10 items-center">
          <motion.div initial={{opacity:0, y:20}} animate={{opacity:1,y:0}} transition={{duration:0.6}}>
            <h1 className="text-3xl sm:text-5xl font-extrabold leading-tight">
              السلام علیکم! میں ہوں <span className="text-slate-900">فیصل</span>
              <br className="hidden sm:block" />
              ویب ڈویلپر & مووی پلیٹ فارم کری ایٹر
            </h1>
            <p className="mt-4 text-slate-600 leading-8">
              میں نے اپنی ویب سائٹ کو ایک پلیٹ فارم میں بدلا ہے جہاں لوگ آن لائن موویز دیکھ سکتے ہیں۔
              آپ یہاں اردو اور انگریزی دونوں زبانوں میں انٹرٹینمنٹ پائیں گے۔
            </p>
            <div className="mt-6 flex flex-wrap gap-3">
              <a href="#movies" className="inline-flex items-center gap-2 px-5 py-3 rounded-2xl bg-slate-900 text-white text-sm font-semibold shadow hover:shadow-md">
                موویز دیکھیں <PlayCircle className="w-5 h-5" />
              </a>
              <a href="#contact" className="inline-flex items-center gap-2 px-5 py-3 rounded-2xl bg-white border border-slate-200 text-sm font-semibold hover:bg-slate-50">
                رابطہ کریں
              </a>
            </div>
          </motion.div>
        </div>
      </section>

      {/* Movies Section */}
      <section id="movies" className="mx-auto max-w-6xl px-4 sm:px-6 py-16">
        <h2 className="text-2xl sm:text-3xl font-bold">آن لائن موویز</h2>
        <p className="mt-2 text-slate-600">سرچ یا کیٹیگری کے ذریعے اپنی پسند کی فلم ڈھونڈیں۔</p>

        {/* Filters */}
        <div className="mt-6 flex flex-col sm:flex-row items-center gap-4">
          <div className="relative w-full sm:w-1/2">
            <Search className="absolute right-3 top-3 w-5 h-5 text-slate-400" />
            <input
              type="text"
              placeholder="مووی تلاش کریں..."
              className="w-full border border-slate-300 rounded-xl px-10 py-2 focus:outline-none focus:ring-2 focus:ring-slate-400"
              value={search}
              onChange={(e) => setSearch(e.target.value)}
            />
          </div>

          <select
            className="w-full sm:w-1/4 border border-slate-300 rounded-xl px-3 py-2 focus:outline-none focus:ring-2 focus:ring-slate-400"
            value={category}
            onChange={(e) => setCategory(e.target.value)}
          >
            <option value="all">تمام کیٹیگریز</option>
            <option value="ایکش">ایکش</option>
            <option value="کامیڈی">کامیڈی</option>
            <option value="ہارر">ہارر</option>
          </select>
        </div>

        {/* Movies Grid */}
        <div className="mt-6 grid md:grid-cols-3 gap-6">
          {filteredMovies.map((movie,i)=>(
            <motion.div key={i} initial={{opacity:0, y:10}} whileInView={{opacity:1, y:0}} viewport={{once:true}} transition={{duration:0.4}} className="rounded-2xl overflow-hidden border border-slate-200 bg-white shadow-sm">
              <div className="aspect-video bg-slate-100">
                <a href={movie.link} target="_blank" rel="noopener noreferrer">
                  <img src={movie.img} alt={movie.title} className="w-full h-full object-cover hover:scale-105 transition-transform" />
                </a>
              </div>
              <div className="p-4">
                <p className="font-semibold">{movie.title}</p>
                <p className="text-xs text-slate-500">{movie.category}</p>
                <a href={movie.link} target="_blank" rel="noopener noreferrer" className="inline-flex items-center gap-2 text-sm font-semibold mt-2 hover:opacity-70">
                  ابھی دیکھیں <PlayCircle className="w-4 h-4" />
                </a>
              </div>
            </motion.div>
          ))}

          {filteredMovies.length === 0 && (
            <p className="col-span-3 text-center text-slate-500">کوئی مووی نہیں ملی</p>
          )}
        </div>
      </section>

      {/* About */}
      <section id="about" className="mx-auto max-w-6xl px-4 sm:px-6 py-16">
        <div className="grid lg:grid-cols-3 gap-8 items-start">
          <div className="lg:col-span-2">
            <h2 className="text-2xl sm:text-3xl font-bold">میرے بارے میں</h2>
            <p className="mt-4 text-slate-600 leading-8">
              میں ایک فرنٹ اینڈ ڈویلپر ہوں جو اب آن لائن مووی پلیٹ فارم پر بھی کام کرتا ہوں۔ میرا مقصد صارفین کو آسان، تیز اور دلچسپ انٹرٹینمنٹ فراہم کرنا ہے۔
            </p>
          </div>
        </div>
      </section>

      {/* Contact */}
      <section id="contact" className="mx-auto max-w-6xl px-4 sm:px-6 py-16">
        <div className="grid lg:grid-cols-2 gap-8">
          <div>
            <h2 className="text-2xl sm:text-3xl font-bold">رابطہ کریں</h2>
            <p className="mt-4 text-slate-600 leading-8">
              اگر آپ چاہتے ہیں کہ اپنی موویز یا ویڈیوز اس پلیٹ فارم پر اپلوڈ کریں تو براہ راست مجھ سے رابطہ کریں۔
            </p>
            <ul className="mt-6 space-y-3 text-sm">
              <li className="flex items-center gap-2"><Mail className="w-4 h-4"/> email@example.com</li>
              <li className="flex items-center gap-2"><Phone className="w-4 h-4"/> +92 300 0000000</li>
              <li className="flex items-center gap-2"><MapPin className="w-4 h-4"/> منڈی بہاؤالدین، پاکستان</li>
            </ul>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="border-t border-slate-200">
        <div className="mx-auto max-w-6xl px-4 sm:px-6 py-8 text-sm flex flex-col sm:flex-row items-center justify-between gap-3">
          <p>© {new Date().getFullYear()} فیصل علی — تمام حقوق محفوظ ہیں۔</p>
          <div className="flex gap-4">
            <a href="#about" className="hover:opacity-70">پرا ئیویسی</a>
            <a href="#services" className="hover:opacity-70">شرائط</a>
          </div>
        </div>
      </footer>
    </div>
  );
}
