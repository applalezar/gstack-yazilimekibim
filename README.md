# gstack-YAZILIM EKİBİ


**gstack benim çalışma yöntemim.** Claude Code'u sanal bir mühendislik ekibine dönüştürüyor: Ürünü yeniden düşünen bir CEO, mimariyi kilitleyen bir mühendislik yöneticisi, yapay zeka hatalarını yakalayan bir tasarımcı, üretim hatalarını bulan bir gözden geçiren, gerçek bir tarayıcı açan bir QA lideri, OWASP + STRIDE denetimleri yapan bir güvenlik görevlisi ve PR'ı gönderen bir sürüm mühendisi. Yirmi üç uzman ve sekiz güçlü araç, hepsi slash komutları, hepsi Markdown, hepsi ücretsiz, MIT lisansı.

Bu benim açık kaynak yazılım fabrikam. Her gün kullanıyorum. Bunu paylaşıyorum çünkü bu araçlar herkesin kullanımına açık olmalı.

Çatallayın. Geliştirin. Kendinize ait yapın. Ve eğer ücretsiz açık kaynak yazılımlardan nefret etmek istiyorsanız - buyurun, ama önce denemenizi tercih ederim.

**Kimler İçin:**
- **Kurucular ve CEO'lar** — özellikle hala ürün piyasaya sürmek isteyen teknik yöneticiler
- **Claude Code'u ilk kez kullananlar** — boş bir komut istemi yerine yapılandırılmış roller
- **Teknik liderler ve kıdemli mühendisler** — her PR'da titiz inceleme, QA ve sürüm otomasyonu

## Hızlı Başlangıç

1. gstack'i kurun (30 saniye — aşağıya bakın)
2. `/office-hours` komutunu çalıştırın — ne geliştirdiğinizi açıklayın
3. Herhangi bir özellik fikri için `/plan-ceo-review` komutunu çalıştırın
4. Değişiklik içeren herhangi bir dal için `/review` komutunu çalıştırın
5. Hazırlık URL'niz için `/qa` komutunu çalıştırın
6. Orada durun. Bunun sizin için uygun olup olmadığını anlayacaksınız.

## Kurulum — 30 saniye

**Gereksinimler:** [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Git](https://git-scm.com/), [Bun](https://bun.sh/) v1.0+, [Node.js](https://nodejs.org/) (yalnızca Windows)

### Adım 1: Makinenize kurun

Claude Code'u açın ve bunu yapıştırın. Claude gerisini halleder.

> gstack'i yükleyin: **`git clone --single-branch --depth 1 https://github.com/applalezar/gstack-yazilimekibim.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup`** komutunu çalıştırın, ardından CLAUDE.md dosyasına, tüm web tarama işlemleri için gstack'in /browse becerisini kullanmayı, mcp\_\_claude-in-chrome\_\_\* araçlarını asla kullanmamayı belirten ve mevcut becerileri listeleyen bir "gstack" bölümü ekleyin: /office-hours, /plan-ceo-review, /plan-eng-review, /plan-design-review, /design-consultation, /design-shotgun, /design-html, /review, /ship, /land-and-deploy, /canary, /benchmark, /browse, /connect-chrome, /qa, /qa-only, /design-review, /setup-browser-cookies, /setup-deploy, /setup-gbrain, /retro, /investigate, /document-release, /document-generate, /codex, /cso, /autoplan, /plan-devex-review, /devex-review, /careful, /freeze, /guard, /unfreeze, /gstack-upgrade, /learn. Ardından, kullanıcıya gstack'i mevcut projeye eklemek isteyip istemediğini sorun, böylece ekip arkadaşları da onu kullanabilir.
`test` komutu, gstack'i otomatik olarak alır ve değişikliği kaydeder:

```bash
(cd ~/.claude/skills/gstack && ./setup --team) && ~/.claude/skills/gstack/bin/gstack-team-init required && git add .claude/ CLAUDE.md && git commit -m "require gstack for AI-assisted work"
```

Deponuzda hiçbir yedek dosya yok, sürüm kayması yok, manuel yükseltme yok. Her Claude Code oturumu, hızlı bir otomatik güncelleme kontrolüyle başlar (saatte bir kez ile sınırlandırılmış, ağ arızalarına karşı güvenli, tamamen sessiz).

Eğer takım arkadaşlarınızı engellemek yerine onlara hatırlatmak isterseniz, `required` yerine `optional` kullanabilirsiniz.

### OpenClaw

OpenClaw, ACP aracılığıyla Claude Code oturumları başlatır, bu nedenle Claude Code'da gstack yüklü olduğunda her gstack becerisi sorunsuz çalışır.
Bunu OpenClaw ajanınıza yapıştırın:

> gstack'i yükleyin: Claude Code için gstack'i yüklemek için `git clone --single-branch --depth 1 [https://github.com/garrytan/gstack.git](https://github.com/applalezar/gstack-yazilimekibim.git) ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup` komutunu çalıştırın. Ardından AGENTS.md dosyasına "Kodlama Görevleri" bölümüne şunu ekleyin: Kodlama işi için Claude Code oturumları başlatırken, oturuma gstack becerilerini kullanmasını söyleyin. Bu örnekleri ekleyin — güvenlik denetimi: "gstack'i yükleyin. /cso komutunu çalıştırın", kod incelemesi: "gstack'i yükleyin. /review komutunu çalıştırın", bir URL'yi QA testi yapın: "gstack'i yükleyin. /qa https://..." komutunu çalıştırın, bir özelliği uçtan uca geliştirin: "gstack'i yükleyin. /autoplan komutunu çalıştırın, planı uygulayın, ardından /ship komutunu çalıştırın", geliştirmeden önce planlama yapın: "gstack'i yükleyin. /office-hours komutunu çalıştırın, ardından /autoplan komutunu çalıştırın. Planı kaydedin, uygulamayın."

**Kurulumdan sonra, OpenClaw temsilcinizle doğal bir şekilde konuşun:**

| Siz söylersiniz | Ne olur |

|---------|-------------|

| "README dosyasındaki yazım hatasını düzeltin" | Basit — Claude Code oturumu, gstack gerekmez |

| "Bu depoda bir güvenlik denetimi çalıştırın" | `Run /cso` ile Claude Code başlatır |

| "Bana bir bildirim özelliği geliştirin" | Claude Code'u /autoplan → implement → /ship ile başlatır |

| "v2 API yeniden tasarımını planlamama yardım edin" | Claude Code'u /office-hours → /autoplan ile başlatır, planı kaydeder |

Gelişmiş dağıtım yönlendirmesi ve gstack-lite/gstack-full komut istemi şablonları için [docs/OPENCLAW.md](docs/OPENCLAW.md) dosyasına bakın.

gstack-lite/gstack-full komut istemi şablonları.

### Yerel OpenClaw Becerileri (ClawHub aracılığıyla)

OpenClaw ajanınızda doğrudan çalışan dört metodoloji becerisi, Claude Code oturumuna gerek yok.
ClawHub'dan yükleyin:

``` clawhub install gstack-openclaw-office-hours gstack-openclaw-ceo-review gstack-openclaw-investigate gstack-openclaw-retro
```

| Beceri | Ne işe yarar |

|-------|-------------|

| `gstack-openclaw-office-hours` | 6 zorlayıcı soruyla ürün sorgulaması |

| `gstack-openclaw-ceo-review` | 4 kapsam moduyla stratejik meydan okuma |

| `gstack-openclaw-investigate` | Kök neden hata ayıklama metodolojisi |

| `gstack-openclaw-retro` | Haftalık mühendislik retrospektifi |

Bunlar konuşma becerileridir. OpenClaw ajanınız bunları doğrudan sohbet yoluyla çalıştırır.

### Diğer Yapay Zeka Ajanları

gstack, yalnızca Claude ile sınırlı kalmayıp 10 farklı yapay zeka kodlama ajanı üzerinde çalışır. Kurulum, hangi ajanların kurulu olduğunu otomatik olarak algılar:

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/gstack
cd ~/gstack && ./setup
```

Veya `./setup --host <ad>` ile belirli bir ajanı hedefleyin:

| Ajan | Bayrak | Becerilerin kurulacağı yer |

|-------|------|-------------------|

| OpenAI Codex CLI | `--host codex` | `~/.codex/skills/gstack-*/` |

| OpenCode | `--host opencode` | `~/.config/opencode/skills/gstack-*/` |

| İmleç | `--host cursor` | `~/.cursor/skills/gstack-*/` |

| Fabrika Droidi | `--host factory` | `~/.factory/skills/gstack-*/` |

| Slate | `--host slate` | `~/.slate/skills/gstack-*/` |

| Kiro | `--host kiro` | `~/.kiro/skills/gstack-*/` |

| Hermes | `--host hermes` | `~/.hermes/skills/gstack-*/` |

| GBrain (mod) | `--host gbrain` | `~/.gbrain/skills/gstack-*/` |

**Başka bir ajan için destek eklemek mi istiyorsunuz?** [docs/ADDING_A_HOST.md](docs/ADDING_A_HOST.md) dosyasına bakın.

Tek bir TypeScript yapılandırma dosyası, sıfır kod değişikliği.

## Çalışmasını görün

```
Siz: Takvimim için günlük bir bilgilendirme uygulaması oluşturmak istiyorum.

Siz: /ofis-saatleri
Claude: [sorunları soruyor - varsayımsal değil, belirli örnekler]

Siz: Birden fazla Google takvimi, güncel olmayan bilgiler içeren etkinlikler, yanlış konumlar.

Hazırlık sonsuza kadar sürüyor ve sonuçlar yeterince iyi değil...

Claude: Çerçeveleme konusunda itiraz edeceğim. "Günlük bilgilendirme
uygulaması" dediniz. Ama aslında tanımladığınız şey kişisel bir başçavuş
yapay zekası.

[Tanımladığınızı fark etmediğiniz 5 yeteneği çıkarır]

[4 önermeyi sorgular — kabul edersiniz, katılmazsınız veya ayarlarsınız]

[Çaba tahminleriyle 3 uygulama yaklaşımı oluşturur]

ÖNERİ: Yarın en dar dilimi gönderin, gerçek kullanımdan öğrenin.

Tam vizyon 3 aylık bir projedir — işe yarayan günlük brifingle başlayın.

[Tasarım belgesini yazar → otomatik olarak alt kademe becerilere aktarır]

Siz: /plan-ceo-incelemesi

[Tasarım belgesini okur, kapsamı sorgular, 10 bölümlü inceleme yapar]

Siz: /plan-mühendis-incelemesi

[Veri akışı, durum makineleri, hata yolları için ASCII diyagramları]

[Test matrisi, arıza modları, güvenlik endişeleri]

Siz: Planı onaylayın. Plan modundan çıkın.

[yaz]
[11 dosyada toplam 2400 satır. ~8 dakika.]

Siz: /review

[OTOMATİK OLARAK DÜZELTİLDİ] 2 sorun. [SORU] Yarış durumu → düzeltmeyi onaylıyorsunuz.

Siz: /qa https://staging.myapp.com

[gerçek tarayıcıyı açar, akışlarda ilerler, bir hata bulur ve düzeltir]

Siz: /ship
Testler: 42 → 51 (+9 yeni). PR: github.com/you/app/pull/42
```

Siz "günlük bilgilendirme uygulaması" dediniz. Ajan, "bir genelkurmay başkanı yapay zekası geliştiriyorsunuz" dedi - çünkü özellik isteğinizi değil, acınızı dinledi. Sekiz komut, baştan sona. Bu bir yardımcı pilot değil. Bu bir ekip.

## Sprint

gstack bir süreçtir, bir araç koleksiyonu değil. Beceriler, bir sprintin çalışma sırasına göre ilerler:

**Düşün → Planla → Oluştur → Gözden Geçir → Test Et → Gönder → Yansıt**

Her beceri bir sonrakini besler. `/office-hours`, `/plan-ceo-review`'ın okuduğu bir tasarım belgesi yazar. `/plan-eng-review`, `/qa`'nın aldığı bir test planı yazar. `/review`, `/ship`'in düzeltildiğini doğruladığı hataları yakalar. Her adım, kendisinden önce ne olduğunu bildiği için hiçbir şey gözden kaçmaz.

| Beceri | Uzmanınız | Ne yaparlar |

|-------|----------------|--------------|

| `/office-hours` | **YC Ofis Saatleri** | Buradan başlayın. Kod yazmadan önce ürününüzü yeniden çerçeveleyen altı zorlayıcı soru. Çerçevelemenize karşı çıkar, varsayımları sorgular, uygulama alternatifleri üretir. Tasarım dokümanı, her bir sonraki beceriye katkıda bulunur. |

| `/plan-ceo-review` | **CEO / Kurucu** | Sorunu yeniden düşünün. Talebin içinde gizlenmiş 10 yıldızlı ürünü bulun. Dört mod: Genişletme, Seçici Genişletme, Kapsamı Koruma, Azaltma. |

| `/plan-eng-review` | **Mühendislik Müdürü** | Mimariyi, veri akışını, diyagramları, uç durumları ve testleri kilitleyin. Gizli varsayımları açığa çıkarın. |

| `/plan-design-review` | **Kıdemli Tasarımcı** | Her tasarım boyutunu 0-10 arasında derecelendirir, 10'un neye benzediğini açıklar, ardından oraya ulaşmak için planı düzenler. Yapay Zeka Eğim tespiti. Etkileşimli — tasarım seçimi başına bir Kullanıcıya Soru Sor. |

| `/plan-devex-review` | **Geliştirici Deneyimi Lideri** | Etkileşimli DX incelemesi: geliştirici personalarını keşfeder, rakiplerin TTHW'sine karşı kıyaslama yapar, sihirli anınızı tasarlar, sürtünme noktalarını adım adım izler. Üç mod: DX GENİŞLETME, DX PARLATMA, DX TRIAGE. 20-45 zorlayıcı soru. |

| `/tasarım-danışmanlığı` | **Tasarım Ortağı** | Sıfırdan eksiksiz bir tasarım sistemi oluşturun. Ortamı araştırır, yaratıcı riskler önerir, gerçekçi ürün maketleri oluşturur. |

| `/inceleme` | **Kıdemli Mühendis** | CI'dan geçen ancak üretimde patlayan hataları bulun. Açık olanları otomatik olarak düzeltir. Eksiklikleri işaretler. |

| `/araştırma` | **Hata Ayıklayıcı** | Sistematik kök neden hata ayıklaması. Demir Kural: araştırma olmadan düzeltme yok. Veri akışını izler, hipotezleri test eder, 3 başarısız düzeltmeden sonra durur. |

| `/tasarım-incelemesi` | **Kod Yazan Tasarımcı** | `/plan-design-review` ile aynı denetimi yapar, ardından bulduğu hataları düzeltir. Atomik commit'ler, öncesi/sonrası ekran görüntüleri. |
| `/devex-review` | **DX Test Cihazı** | Canlı geliştirici deneyimi denetimi. Gerçekten de işe alım sürecinizi test eder: dokümanlarda gezinir, başlangıç ​​akışını dener, TTHW'yi (son kullanma tarihi) ölçer, hataların ekran görüntülerini alır. `/plan-devex-review` puanlarıyla karşılaştırır - planınızın gerçekliğe uyup uymadığını gösteren geri bildirim. |

| `/design-shotgun` | **Tasarım Gezgini** | "Bana seçenekleri göster." 4-6 yapay zeka maket varyantı oluşturur, tarayıcınızda bir karşılaştırma panosu açar, geri bildirimlerinizi toplar ve yineler. Beğendiğiniz şeyleri öğrenir. Bir şeyi beğenene kadar tekrarlayın, ardından `/design-html`'e verin. |

| `/design-html` | **Tasarım Mühendisi** | Bir maketi gerçekten çalışan üretim HTML'sine dönüştürün. Ön hesaplamalı düzen: metin yeniden düzenlenir, yükseklikler ayarlanır, düzenler dinamiktir. 30 KB, sıfır bağımlılık. React/Svelte/Vue'yu algılar. Tasarım türüne göre (açılış sayfası, kontrol paneli, form) akıllı API yönlendirmesi. Çıktı gönderilebilir, demo değil. |
| `/qa` | **QA Lideri** | Uygulamanızı test edin, hataları bulun, atomik commit'lerle düzeltin, tekrar doğrulayın. Her düzeltme için otomatik olarak regresyon testleri oluşturur. |
| `/qa-only` | **QA Raporlayıcısı** | /qa ile aynı metodoloji, ancak yalnızca raporlama. Kod değişiklikleri olmadan saf hata raporu. |

| `/pair-agent` | **Çoklu Ajan Koordinatörü** | Tarayıcınızı herhangi bir yapay zeka ajanıyla paylaşın. Tek komut, tek yapıştırma, bağlantı kuruldu. OpenClaw, Hermes, Codex, Cursor veya curl çalıştırabilen herhangi bir şeyle çalışır. Her ajan kendi sekmesini alır. Her şeyi izleyebilmeniz için otomatik olarak başlık modu başlatır. Uzak ajanlar için otomatik olarak ngrok tüneli başlatır. Kapsamlı belirteçler, sekme izolasyonu, hız sınırlama, etkinlik atfı. |

| `/cso` | **Baş Güvenlik Sorumlusu** | OWASP Top 10 + STRIDE tehdit modeli. Sıfır gürültü: 17 yanlış pozitif dışlama, 8/10+ güven eşiği, bağımsız bulgu doğrulaması. Her bulgu somut bir istismar senaryosu içerir. |

| `/ship` | **Sürüm Mühendisi** | Ana dosyayı senkronize et, testleri çalıştır, kapsama denetimi yap, gönder, PR aç. Test çerçeveleriniz yoksa test çerçevelerini başlatır. |

| `/land-and-deploy` | **Sürüm Mühendisi** | PR'yi birleştir, CI'yı bekle ve dağıt, üretim sağlığını doğrula. "Onaylandı"dan "üretimde doğrulandı"ya tek komut. |

| `/canary` | **SRE** | Dağıtım sonrası izleme döngüsü. Konsol hatalarını izler, her Performans gerilemeleri ve sayfa hataları. |

| `/benchmark` | **Performans Mühendisi** | Temel sayfa yükleme sürelerini, Temel Web Yaşam Verilerini ve kaynak boyutlarını belirleyin. Her PR'da önce/sonra karşılaştırması yapın. |

| `/document-release` | **Teknik Yazar** | Yeni gönderdiğiniz sürüme uygun olarak tüm proje belgelerini güncelleyin. Eski README dosyalarını otomatik olarak yakalar. PR gövdesinde boşlukların görünür olması için bir Diataxis kapsama haritası (referans / nasıl yapılır / eğitim / açıklama) oluşturur. |

| `/document-generate` | **Belge Yazarı** | Diataxis çerçevesini kullanarak eksik belgeleri sıfırdan oluşturun. Önce kod tabanını araştırır, ardından kodla gerçekten eşleşen referans / nasıl yapılır / eğitim / açıklama belgeleri yazar. Kapsama haritası boşluklar bulduğunda `/document-release`'den bağımsız olarak veya zincirleme olarak çağrılabilir. Daha fazla bilgi edinin: [eğitim](docs/tutorial-document-generate.md) • [nasıl yapılır](docs/howto-document-a-shipped-feature.md) • [Diataxis neden kullanılır](docs/explanation-diataxis-in-gstack.md). |

| `/retro` | **Mühendislik Yöneticisi** | Takım odaklı haftalık retrospektif. Kişi başı dökümler, yayın serileri, test sağlığı trendleri, büyüme fırsatları. `/retro global` tüm projelerinizde ve yapay zeka araçlarınızda (Claude Code, Codex, Gemini) çalışır. |

| `/browse` | **Kalite Güvence Mühendisi** | Ajanlara göz verin. Gerçek Chromium tarayıcı, gerçek tıklamalar, gerçek ekran görüntüleri. Komut başına ~100 ms. `/open-gstack-browser`, kenar çubuğu, bot karşıtı gizlilik ve otomatik model yönlendirme ile GStack Tarayıcıyı başlatır. |

| `/setup-browser-cookies` | **Oturum Yöneticisi** | Gerçek tarayıcınızdan (Chrome, Arc, Brave, Edge) çerezleri başsız oturuma aktarın. Kimlik doğrulamalı sayfaları test edin. |

| `/autoplan` | **İnceleme Hattı** | Tek komutla, tamamen incelenmiş plan. Kodlanmış karar ilkeleriyle CEO → tasarım → mühendislik incelemesini otomatik olarak çalıştırır. Onayınız için yalnızca deneme kararlarını sunar. |

| `/learn` | **Bellek** | gstack'in oturumlar arasında öğrendiklerini yönetin. Projeye özgü kalıpları, tuzakları ve tercihleri ​​inceleyin, arayın, budayın ve dışa aktarın. Öğrenmeler oturumlar arasında birikerek gstack'in zamanla kod tabanınızda daha akıllı hale gelmesini sağlar. |

### Hangi incelemeyi kullanmalıyım?

| Şunlar için geliştirme... | Planlama aşaması (koddan önce) | Canlı denetim (teslimattan sonra) |
|-----------------|--------------------------|----------------------------|

| **Son Kullanıcılar** (Kullanıcı Arayüzü, web uygulaması, mobil) | `/plan-design-review` | `/design-review` |

| **Geliştiriciler** (API, CLI, SDK, dokümanlar) | `/plan-devex-review` | `/devex-review` |

| **Mimari** (veri akışı, performans, testler) | `/plan-eng-review` | `/review` |

| **Yukarıdakilerin tümü** | `/autoplan` (CEO → tasarım → mühendislik → DX çalıştırır, hangilerinin geçerli olduğunu otomatik olarak algılar) | — |

### Güçlü Araçlar

| Beceri | Ne İşe Yarar |

|-------|-------------|

| `/codex` | **İkinci Görüş** — OpenAI Codex CLI'dan bağımsız kod incelemesi. Üç mod: inceleme (geçti/kaldı kapısı), düşmanca meydan okuma ve açık danışma. Hem `/review` hem de `/codex` çalıştırıldığında çapraz model analizi. |

| `/careful` | **Güvenlik Bariyerleri** — yıkıcı komutlardan önce uyarı verir (rm -rf, DROP TABLE, force-push). Etkinleştirmek için "be careful" deyin. Herhangi bir uyarıyı geçersiz kılın. |

| `/freeze` | **Düzenleme Kilidi** — dosya düzenlemelerini tek bir dizinle sınırlandırır. Hata ayıklama sırasında kapsam dışındaki kazara değişiklikleri önler. |

| `/guard` | **Tam Güvenlik** — `/careful` + `/freeze` tek bir komutta. Üretim çalışmaları için maksimum güvenlik. |

| `/unfreeze` | **Kilidi Aç** — `/freeze` sınırını kaldırın. |

| `/open-gstack-browser` | **GStack Tarayıcı** — kenar çubuğu, bot karşıtı gizlilik, otomatik model yönlendirme (eylemler için Sonnet, analiz için Opus), tek tıklamayla çerez içe aktarma ve Claude Code entegrasyonu ile GStack Tarayıcıyı başlatın. Sayfaları temizleyin, akıllı ekran görüntüleri alın, CSS'yi düzenleyin ve bilgileri terminalinize geri gönderin. |

| `/setup-deploy` | **Dağıtım Yapılandırıcısı** — `/land-and-deploy` için tek seferlik kurulum. Platformunuzu, üretim URL'nizi ve dağıtım komutlarınızı algılar. |

| `/setup-gbrain` | **GBrain Kurulumu** — sıfırdan 5 dakikadan kısa sürede gbrain'i çalıştırmaya başlayın. PGLite yerel, Supabase mevcut URL veya Yönetim API'si aracılığıyla yeni bir Supabase projesi otomatik olarak sağlayın. Claude Code için MCP kaydı + depo başına güven üçlüsü (okuma-yazma/sadece okuma/reddetme). [Tam kılavuz](USING_GBRAIN_WITH_GSTACK.md). |

| `/sync-gbrain` | **Gbrain'i Güncel Tutun** — bu deponun kodunu `gbrain sources add` + `gbrain sync --strategy code` komutlarıyla gbrain'e yeniden indeksleyin, CLAUDE.md dosyasındaki `## GBrain Arama Kılavuzu` bloğunu yenileyin ve yetenek kontrolü başarısız olduğunda kılavuzu otomatik olarak kaldırın. `--incremental` (varsayılan), `--full`, `--dry-run`. Tekrarlanabilir; tekrar çalıştırmak güvenlidir. |

| `/gstack-upgrade` | **Kendi Kendini Güncelleyen** — gstack'i en son sürüme yükseltin. Genel ve satıcıya özel kurulumu algılar, ikisini de senkronize eder, nelerin değiştiğini gösterir. |

| `/ios-qa` | **iOS Canlı Cihaz QA (v1.43.0.0+)** — Uygulamada yerleşik bir `StateServer` aracılığıyla USB CoreDevice üzerinden gerçek bir iPhone'u çalıştırın. Swift kaynak kodunu okuyun, kod üretimiyle `@Observable` erişimcilerini oluşturun, ajan döngüsünü çalıştırın. İsteğe bağlı `--tailnet` bayrağı, cihazı OpenClaw'a veya Tailscale kuyruk ağınızdaki herhangi bir HTTP özellikli ajana gösterir, böylece uzak ajanlar donanıma hiç dokunmadan iOS QA çalıştırabilir. Yetenek katmanı izin listesi (gözlemle/etkileşim kur/değiştir/geri yükle) ), cihaz başına oturum kilidi, denetim günlüğü. |

| `/ios-fix`, `/ios-design-review`, `/ios-clean`, `/ios-sync` | iOS hata düzeltme döngüsü, tasarımcı gözüyle HIG denetimi, hata ayıklama köprüsü temizliği ve erişimci yeniden senkronizasyonu. Bkz. `docs/skills.md`. Uçtan uca kılavuz: [docs/howto-ios-testing-with-gstack.md](docs/howto-ios-testing-with-gstack.md). |

### Yeni ikili dosyalar (v0.19)

Eğik çizgi komut becerilerinin ötesinde, gstack, bir oturumun içinde yer almayan iş akışları için bağımsız CLI'lar sunar:

| Komut | Ne yapar |

|---------|-------------|

| `gstack-model-benchmark` | **Modeller Arası Karşılaştırma** — Aynı komut istemini Claude, GPT (Codex CLI aracılığıyla) ve Gemini üzerinden çalıştırın; gecikmeyi, belirteçleri, maliyeti ve (isteğe bağlı olarak) LLM-judge kalite puanını karşılaştırın. Kimlik doğrulama sağlayıcı başına algılanır, kullanılamayan sağlayıcılar sorunsuz bir şekilde atlanır. Çıktı tablo, JSON veya markdown olarak verilir. `--dry-run` API çağrıları harcamadan bayrakları + kimlik doğrulamayı doğrular. |

| `gstack-taste-update` | **Tasarım zevki öğrenimi** — `/design-shotgun`'dan gelen onayları ve retleri kalıcı bir proje zevki profiline yazar. Haftada %5 azalır. Gelecekteki varyant üretimine geri besleme yapar, böylece sistem aslında ne seçtiğinizi öğrenir. |

| `gstack-ios-qa-daemon` | **iOS QA arka plan programı** — Bir aracı ile USB CoreDevice üzerinden bağlı bir iPhone arasında Mac tarafı aracı. Varsayılan olarak geri döngü; `--tailnet`, kimlik doğrulamalı yetenek katmanlarına sahip Tailscale'e yönelik bir dinleyici açar. `~/.gstack/ios-qa-daemon.pid` üzerinde flock aracılığıyla tek örnek. [docs/howto-ios-testing-with-gstack.md](docs/howto-ios-testing-with-gstack.md) adresine bakın. |

| `gstack-ios-qa-mint` | **iOS izin listesi yöneticisi** — tailnet izin listesi için sahip-izin verme CLI'sı. `~/.gstack/ios-qa-allowlist.json`'a karşı `grant`/`revoke`/`list` (mod 0600). Uzak aracılar asla otomatik olarak izin listesine ekleme yapmaz; bu, açık niyet yoludur. |

### Sürekli kontrol noktası modu (isteğe bağlı, varsayılan olarak yerel)

`gstack-config set checkpoint_mode continuous` komutunu ayarlayın ve beceriler, `WIP:` öneki ve yapılandırılmış bir `[gstack-context]` gövdesi (kararlar, kalan işler, başarısız yaklaşımlar) ile birlikte çalışmanızı otomatik olarak kaydeder. Çökmelere ve bağlam değişikliklerine karşı dayanıklıdır. `/context-restore`, oturum durumunu yeniden oluşturmak için bu commit'leri okur. `/ship`, PR'dan önce WIP commit'lerini filtreleyerek sıkıştırır (WIP olmayan commit'leri koruyarak), böylece bisect temiz kalır. Push, `checkpoint_push=true` ile isteğe bağlıdır — varsayılan olarak yalnızca yereldir, böylece her WIP commit'inde CI'yi tetiklemezsiniz.

### Alan Becerileri + Ham CDP Kaçış Yolu

İki yeni tarayıcı temel öğesi, gstack aracısını zaman içinde birleştirir:

- **`$B domain-skill save`** — aracı, bir sonraki sefer o ana bilgisayar adını ziyaret ettiğinde otomatik olarak tetiklenen site başına bir not kaydeder (örneğin, "LinkedIn'in Başvur düğmesi bir iframe içinde yer alıyor"). Karantinaya alınır → 3 başarılı kullanımdan sonra etkin hale gelir → `$B domain-skill promote-to-global` aracılığıyla isteğe bağlı olarak projeler arası yükseltme. Depolama, `/learn`'ün proje başına öğrenme dosyasıyla birlikte bulunur. Tam referans: **[docs/domain-skills.md](docs/domain-skills.md)**.

- **`$B cdp <Domain.method>`** — derlenmiş komutların gözden kaçırdığı nadir durumlar için ham Chrome Geliştirici Araçları Protokolü kaçış yolu. Varsayılan olarak reddetme: Metotlar, tek satırlık bir gerekçeyle `browse/src/cdp-allowlist.ts` dosyasına açıkça eklenmelidir. İki katmanlı mutex, tarayıcı kapsamlı CDP çağrılarını sekme başına yapılan çalışmalara karşı serileştirir. Veri sızdırma metotlarının çıktısı, GÜVENİLMEYEN zarfına sarılır.

> Rails, allowlist, daemon olmadan, sadece agent'tan Chrome'a ​​ince bir taşıma ile ham CDP mi istiyorsunuz? [browser-use/browser-harness-js](https://github.com/browser-use/browser-harness-js) farklı bir felsefeye (agent tarafından yazılan yardımcılar vs. gstack'in derlenmiş komutları) sahiptir ve gstack'in güvenlik yığınını istemiyorsanız iyi bir seçenektir. İkisi birlikte var olabilir: gstack'in `$B cdp` ve harness, Playwright'ın `newCDPSession`'ı aracılığıyla aynı Chrome'a ​​bağlanabilir.

**[Her beceri için örnekler ve felsefe içeren derinlemesine incelemeler →](docs/skills.md)**

### Karpathy'nin dört hata modu? Zaten ele alındı.

Andrej Karpathy'nin [Yapay Zeka kodlama kuralları](https://github.com/forrestchang/andrej-karpathy-skills) (17K yıldız) dört hata modunu ele alıyor: yanlış varsayımlar, aşırı karmaşıklık, ortogonal düzenlemeler, bildirimsel yerine zorunlu yaklaşım. gstack'in iş akışı becerileri dördünü de uyguluyor. `/office-hours` kod yazılmadan önce varsayımları açıkça ortaya koyuyor. Karışıklık Protokolü, Claude'un mimari kararlar konusunda tahmin yürütmesini engelliyor. `/review` gereksiz karmaşıklığı ve aceleyle yapılan düzenlemeleri yakalıyor. `/ship` görevleri, test öncelikli yürütme ile doğrulanabilir hedeflere dönüştürüyor. Eğer zaten Karpathy tarzı CLAUDE.md kuralları kullanıyorsanız, gstack, bu kuralların yalnızca tek bir komut için değil, tüm sprintler boyunca geçerli olmasını sağlayan iş akışı uygulama katmanıdır.

## Paralel Sprintler

gstack tek bir sprint ile iyi çalışır. On sprintin aynı anda çalışmasıyla işler ilginçleşir.

**Tasarım her şeyin merkezindedir.** `/design-consultation`, tasarım sisteminizi sıfırdan oluşturur, mevcut seçenekleri araştırır, yaratıcı riskler önerir ve `DESIGN.md` dosyasını yazar. Ancak asıl sihir, shotgun'dan HTML'ye dönüştürme işlemidir.

**`/design-shotgun`, keşfetme yönteminizdir.** Ne istediğinizi tanımlarsınız. GPT Image kullanarak 4-6 yapay zeka maket varyantı oluşturur. Ardından bir karşılaştırma kutusu açar. Tarayıcınızda tüm varyantları yan yana görüntüleyin. Favorilerinizi seçin, geri bildirim bırakın ("daha fazla boşluk", "daha kalın başlık", "gradyanı kaldır") ve yeni bir tur oluşturulur. Bir şeyi beğenene kadar tekrarlayın. Birkaç turdan sonra tat hafızası devreye girer ve gerçekten beğendiğiniz şeye doğru eğilim göstermeye başlar. Artık vizyonunuzu kelimelerle tanımlayıp yapay zekanın anlamasını ummaya gerek yok. Seçenekleri görürsünüz, iyi olanları seçersiniz ve görsel olarak yinelersiniz.

**`/design-html` bunu gerçeğe dönüştürüyor.** Onaylanmış maketi (`/design-shotgun`'dan, bir CEO planından, bir tasarım incelemesinden veya sadece bir açıklamadan) alın ve üretim kalitesinde HTML/CSS'ye dönüştürün. Bir görüntüleme alanı genişliğinde iyi görünen ve her yerde bozulan yapay zeka HTML'si değil. Bu, hesaplanmış metin düzeni için Pretext kullanır: metin yeniden boyutlandırıldığında gerçekten yeniden akar, yükseklikler içeriğe göre ayarlanır, düzenler dinamiktir. 30 KB ek yük, sıfır bağımlılık. Çerçeveyi (React, Svelte, Vue) algılar ve doğru formatı çıkarır. Akıllı API yönlendirmesi, bir açılış sayfası, kontrol paneli, form veya kart düzeni olup olmadığına bağlı olarak farklı Pretext kalıpları seçer. Çıktı, bir demo değil, gerçekten göndereceğiniz bir şeydir.

**`/qa` büyük bir dönüm noktası oldu.** 6'dan 12'ye paralel çalışan sayısına ulaşmamı sağladı. Claude Code'un *"SORUNU GÖRÜYORUM"* demesi ve ardından gerçekten düzeltmesi, bir regresyon testi oluşturması ve düzeltmeyi doğrulaması, çalışma şeklimi değiştirdi. Artık ajanın gözleri var.

**Akıllı inceleme yönlendirmesi.** Tıpkı iyi yönetilen bir girişimde olduğu gibi: CEO'nun altyapı hata düzeltmelerine bakmasına gerek yok, arka uç değişiklikleri için tasarım incelemesi gerekmiyor. gstack, hangi incelemelerin yapıldığını takip eder, uygun olanı bulur ve akıllıca olanı yapar. İnceleme Hazırlık Paneli, göndermeden önce nerede olduğunuzu gösterir.

**Her şeyi test edin.** `/ship`, projenizde yoksa sıfırdan test çerçeveleri oluşturur. Her `/ship` çalıştırması bir kapsama denetimi üretir. Her `/qa` hata düzeltmesi bir regresyon testi oluşturur. %100 test kapsamı hedeftir — testler, riskli kodlama yerine güvenli bir şekilde kod yazmayı sağlar.

**`/document-release`, hiç sahip olmadığınız mühendisinizdir.** Projenizdeki her belge dosyasını okur, farkı çapraz referanslar ve sapma gösteren her şeyi günceller. README, ARCHITECTURE, CONTRIBUTING, CLAUDE.md, TODOS — hepsi otomatik olarak güncel tutulur. Ve şimdi `/ship` bunu otomatik olarak çağırır — belgeler ekstra bir komut olmadan güncel kalır.

**Gerçek tarayıcı modu.** `/open-gstack-browser`, yapay zeka kontrollü, bot karşıtı gizlilik, özel marka ve yerleşik kenar çubuğu uzantısına sahip bir Chromium olan GStack Tarayıcısını başlatır. Google ve NYTimes gibi siteler captcha olmadan çalışır. Menü çubuğunda "Test için Chrome" yerine "GStack Tarayıcı" yazıyor. Normal Chrome'unuz dokunulmadan kalıyor. Mevcut tüm tarama komutları değişmeden çalışıyor. `$B disconnect` başsız moda geri dönüyor. Tarayıcı, pencere açık olduğu sürece aktif kalıyor... çalışırken onu öldüren bir boşta kalma zaman aşımı yok.

**Yan panel ajanı — yapay zeka tarayıcı asistanınız.** Chrome yan panelinde doğal dil yazın ve bir alt Claude örneği bunu yürütür. "Ayarlar sayfasına gidin ve ekran görüntüsünü alın." "Bu formu test verileriyle doldurun." "Bu listedeki her öğeyi inceleyin ve fiyatları çıkarın." Yan panel otomatik olarak doğru modele yönlendirir: Hızlı işlemler için Sonnet (tıklama, gezinme, ekran görüntüsü alma) ve okuma ve analiz için Opus. Her görev için 5 dakikaya kadar süre verilir. Yan panel ajanı izole bir oturumda çalışır, bu nedenle ana Claude Code pencerenize müdahale etmez. Yan panel altbilgisinden tek tıklamayla çerez içe aktarma.

**Kişisel otomasyon.** Yan panel ajanı sadece geliştirme iş akışları için değildir. Örnek: "Çocuğumun okulunun veli portalına göz atın ve diğer tüm velilerin adlarını, telefon numaralarını ve fotoğraflarını Google Kişilerime ekleyin." Kimlik doğrulama için iki yol: (1) başlıklandırılmış tarayıcıda bir kez oturum açın, oturumunuz devam eder veya (2) gerçek Chrome'unuzdan çerezleri içe aktarmak için kenar çubuğu altbilgisindeki "çerezler" düğmesine tıklayın. Kimlik doğrulama tamamlandıktan sonra, Claude dizini gezer, verileri çıkarır ve kişileri oluşturur.

**İstem enjeksiyon savunması.** Düşman web sayfaları kenar çubuğu aracınızı ele geçirmeye çalışır. gstack katmanlı bir savunma sunar: tarayıcıyla birlikte gelen 22 MB'lık bir ML sınıflandırıcı, her sayfayı ve araç çıktısını yerel olarak tarar, bir Claude Haiku transkript kontrolü tüm konuşma şekli üzerinde oy kullanır, sistem isteminde rastgele bir canary belirteci, metin, araç argümanları, URL'ler ve dosya yazmaları genelinde oturum sızdırma girişimlerini yakalar ve bir karar birleştirici, engellemeden önce iki sınıflandırıcının aynı fikirde olmasını gerektirir (Stack Overflow tarzı talimat sayfalarında tek model yanlış pozitiflerini önler). Kenar çubuğu başlığındaki kalkan simgesi durumu gösterir (yeşil/sarı/kırmızı). 2/3 anlaşması için `GSTACK_SECURITY_ENSEMBLE=deberta` aracılığıyla 721MB DeBERTa-v3 kümesine katılın. Acil durum kapatma anahtarı: `GSTACK_SECURITY_OFF=1`. Tam yığın için [ARCHITECTURE.md](ARCHITECTURE.md#prompt-injection-defense-sidebar-agent) dosyasına bakın.

**Yapay zeka takıldığında tarayıcı geçişi.** Bir CAPTCHA, kimlik doğrulama duvarı veya MFA istemiyle mi karşılaştınız? `$B handoff`, tüm çerezleriniz ve sekmeleriniz bozulmadan aynı sayfada görünür bir Chrome açar. Sorunu çözün, tel Claude, işin bitti, `$B resume` kaldığı yerden devam ediyor. Hatta ajan, art arda 3 başarısız denemeden sonra otomatik olarak bunu öneriyor.

**`/pair-agent` ajanlar arası koordinasyon sağlar.** Claude Code'dasınız. Ayrıca OpenClaw, Hermes veya Codex de çalışıyor. İkisinin de aynı web sitesine bakmasını istiyorsunuz. `/pair-agent` yazın, ajanınızı seçin ve bir GStack Tarayıcı penceresi açılır, böylece izleyebilirsiniz. Beceri bir talimat bloğu yazdırır. Bu bloğu diğer ajanın sohbetine yapıştırın. Tek kullanımlık bir kurulum anahtarını bir oturum belirteciyle değiştirir, kendi sekmesini oluşturur ve taramaya başlar. Her iki ajanın da aynı tarayıcıda, her birinin kendi sekmesinde çalıştığını, hiçbirinin diğerine müdahale edemediğini görürsünüz. ngrok yüklüyse, tünel otomatik olarak başlar, böylece diğer ajan tamamen farklı bir makinede olabilir. Aynı makinedeki ajanlar, kimlik bilgilerini doğrudan yazan sıfır sürtünmeli bir kısayol elde eder. Bu, farklı tedarikçilerden gelen yapay zeka ajanlarının gerçek güvenlik önlemleriyle (kapsamlı belirteçler, sekme izolasyonu, hız sınırlaması, alan adı kısıtlamaları ve etkinlik atfı) ortak bir tarayıcı üzerinden koordinasyon sağlayabildiği ilk seferdir.

**Çoklu Yapay Zeka İkinci Görüşü.** `/codex`, OpenAI'nin Codex CLI'sinden bağımsız bir inceleme alır; aynı farkı inceleyen tamamen farklı bir yapay zeka. Üç mod: geçme/kalma kapısı ile kod incelemesi, kodunuzu aktif olarak bozmaya çalışan düşmanca meydan okuma ve oturum sürekliliği ile açık danışma. Hem `/review` (Claude) hem de `/codex` (OpenAI) aynı dalı incelediğinde, hangi bulguların örtüştüğünü ve hangilerinin her birine özgü olduğunu gösteren bir modeller arası analiz elde edersiniz.

**İhtiyaca göre güvenlik önlemleri.** "Dikkatli olun" deyin ve `/careful` herhangi bir yıkıcı komuttan önce uyarı verir — rm -rf, DROP TABLE, force-push, git reset --hard. `/freeze` komutu, hata ayıklama sırasında Claude'un yanlışlıkla ilgisiz kodları "düzeltmesini" önlemek için düzenlemeleri tek bir dizine kilitler. `/guard` komutu her ikisini de etkinleştirir. `/investigate` komutu ise incelenen modüle otomatik olarak kilitler.

**Proaktif beceri önerileri.** gstack, hangi aşamada olduğunuzu (beyin fırtınası, inceleme, hata ayıklama, test etme) fark eder ve doğru beceriyi önerir. Beğenmediniz mi? "Önermeyi durdur" deyin ve oturumlar arasında hatırlar.

## 10-15 paralel sprint

gstack, tek bir sprint ile güçlüdür. On sprinti aynı anda çalıştırarak dönüştürücü bir etki yaratır.

[Conductor](https://conductor.build), her biri kendi izole çalışma alanında olmak üzere birden fazla Claude Code oturumunu paralel olarak çalıştırır. Bir oturumda yeni bir fikir üzerinde `/office-hours` çalıştırılıyor, bir diğerinde bir PR üzerinde `/review` yapılıyor, üçüncüsünde bir özellik uygulanıyor, dördüncüsünde test ortamında `/qa` çalıştırılıyor ve altı oturumda daha farklı dallar üzerinde çalışılıyor. Hepsi aynı anda. Düzenli olarak 10-15 paralel sprint çalıştırıyorum - şu anda pratik maksimum bu.

Sprint yapısı, paralelliği mümkün kılan şeydir. Bir süreç olmadan, on ajan on kaos kaynağıdır. Bir süreçle - düşün, planla, oluştur, incele, test et, gönder - her ajan tam olarak ne yapacağını ve ne zaman duracağını bilir. Onları bir CEO'nun bir ekibi yönettiği gibi yönetirsiniz: önemli kararları kontrol edin, gerisini kendi haline bırakın.

### Sesli giriş (AquaVoice, Whisper, vb.)

gstack becerilerinin sese uygun tetikleyici ifadeleri vardır. İstediğinizi doğal bir şekilde söyleyin -
"güvenlik kontrolü yap", "web sitesini test et", "mühendislik incelemesi yap" - ve
doğru beceri etkinleşir. Eğik çizgi komut adlarını veya kısaltmaları hatırlamanıza gerek yok.

## Kaldırma

### Seçenek 1: Kaldırma betiğini çalıştırın

Eğer gstack makinenizde kuruluysa:

```bash
~/.claude/skills/gstack/bin/gstack-uninstall
```

Bu, becerileri, sembolik bağlantıları, genel durumu (`~/.gstack/`), projeye özgü durumu, tarama servislerini ve geçici dosyaları yönetir. Yapılandırmayı ve analizleri korumak için `--keep-state` kullanın. Onaylamayı atlamak için `--force` kullanın.

### Seçenek 2: Manuel kaldırma (yerel depo yok)

Eğer depoyu klonlamadıysanız (örneğin, Claude Code kopyası aracılığıyla kurduysanız ve daha sonra klonu sildiyseniz):

```bash
# 1. Browse servislerini durdurun
pkill -f "gstack.*browse" 2>/dev/null || true

# 2. SKILL.md dosyası gstack/ dizinine işaret eden beceri başına dizinleri kaldırın
find ~/.claude/skills -mindepth 1 -maxdepth 1 -type d ! -name gstack 2>/dev/null |

while IFS= read -r dir; do

link="$dir/SKILL.md"

[ -L "$link" ] || continue
target=$(readlink "$link" 2>/dev/null) || devam et
durum "$target" içinde

gstack/*|*/gstack/*)

rm -f "$link"
rmdir "$dir" 2>/dev/null || true

;;
esac
tamamlandı

# 3. gstack'i kaldır
rm -rf ~/.claude/skills/gstack

# 4. Genel durumu kaldır
rm -rf ~/.gstack

# 5. Entegrasyonları kaldır (hiç kurmadığınız entegrasyonları atlayın)
rm -rf ~/.codex/skills/gstack* 2>/dev/null
rm -rf ~/.factory/skills/gstack* 2>/dev/null
rm -rf ~/.kiro/skills/gstack* 2>/dev/null
rm -rf ~/.openclaw/skills/gstack* 2>/dev/null

# 6. Geçici dosyaları kaldır
rm -f /tmp/gstack-* 2>/dev/null

# 7. Proje bazında temizlik (her proje kökünden çalıştırın)
rm -rf .gstack `.gstack-worktrees .claude/skills/gstack 2>/dev/null`
`rm -rf .agents/skills/gstack* .factory/skills/gstack* 2>/dev/null`
```

### CLAUDE.md dosyasını temizleme

Kaldırma betiği CLAUDE.md dosyasını düzenlemez. Gstack'in eklendiği her projede, `## gstack` ve `## Ski` satırlarını kaldırın.
`routing` bölümleri.

### Playwright

`~/Library/Caches/ms-playwright/` (macOS) diğer araçlar tarafından paylaşılabileceği için yerinde bırakılmıştır. Başka bir şeye ihtiyaç duyulmuyorsa kaldırın.

---

Ücretsiz, MIT lisanslı, açık kaynak. Premium katman yok, bekleme listesi yok.

Yazılım geliştirme yöntemimi açık kaynak olarak yayınladım. Çatalını alıp kendinize ait hale getirebilirsiniz.

> **İşe alım yapıyoruz.** Yapay zeka kodlama hızında gerçek ürünler geliştirmek ve gstack'i güçlendirmeye yardımcı olmak ister misiniz?

> YC'de çalışmaya gelin — [ycombinator.com/software](https://ycombinator.com/software)
> Son derece rekabetçi maaş ve hisse senedi. San Francisco, Dogpatch Bölgesi.

## GBrain — Kodlama Ajanınız İçin Kalıcı Bilgi

[GBrain](https://github.com/garrytan/gbrain), yapay zeka ajanları için kalıcı bir bilgi tabanıdır — bunu, ajanınızın oturumlar arasında gerçekten sakladığı bellek olarak düşünün. GStack, sıfırdan "çalışıyor, ajanım çağırabilir" noktasına tek komutla ulaşmanızı sağlar.

```bash
/setup-gbrain
```

Dört yol, birini seçin:

- **Supabase, mevcut URL** — bulut ajanınız zaten bir beyin oluşturdu; Oturum Havuzu URL'sini yapıştırın, artık bu dizüstü bilgisayar aynı verileri kullanıyor.

- **Supabase, otomatik sağlama** — bir Supabase Kişisel Erişim Belirteci yapıştırın; beceri yeni bir proje oluşturur, sağlıklı olup olmadığını kontrol eder, havuz URL'sini alır ve `gbrain init` komutuna iletir. Uçtan uca ~90 saniye.

- **PGLite yerel** — sıfır hesap, sıfır ağ, ~30 saniye. Bu Mac'te yalnızca izole edilmiş bir gbrain. Önce deneme amaçlı kullanım için harika; daha sonra `/setup-gbrain --switch` komutuyla Supabase'e geçiş yapabilirsiniz.

- **Uzak gbrain MCP** — gbrain'iniz başka bir makinede (Tailscale, ngrok, dahili LAN) veya bir ekip arkadaşınızın sunucusunda çalışır; bir MCP URL'si ve taşıyıcı belirteci yapıştırın. İsteğe bağlı olarak, bölünmüş motor modunda sembol duyarlı kod araması için yerel bir PGLite ile eşleştirin. Yerel bir veritabanı kurmadan makineler arası bellek için en iyisidir.

Başlatıldıktan sonra, beceri, gbrain'i Claude Code için bir MCP sunucusu olarak kaydetmeyi teklif eder (`claude mcp add gbrain -- gbrain serve`), böylece `gbrain search`, `gbrain put` vb. komutlar birinci sınıf yazılı araçlar olarak görünür — bash shell komutları olarak değil.

**Beyni güncel tutmak.** Herhangi bir depodan `/sync-gbrain` komutunu çalıştırarak kodunu gbrain'e yeniden indeksleyebilirsiniz (varsayılan olarak artımlı, tam yeniden indeksleme için `--full`, önizleme için `--dry-run`). Bu beceri, `gbrain sources add` komutuyla geçerli çalışma dizinini birleşik kaynak olarak kaydeder, `gbrain sync --strategy code` komutunu çalıştırır ve projenizin CLAUDE.md dosyasına `## GBrain Arama Kılavuzu` bloğu yazar, böylece aracı Grep yerine `gbrain search`/`code-def`/`code-refs` komutlarını tercih eder. Yetenek kontrolü başarısız olursa blok otomatik olarak kaldırılır — kurulu olmayan araçlara işaret eden eski kılavuzlar olmaz.

**Uzak sunucu başına güven politikası.** Makinenizdeki her depo üç kademeden birini alır:

- `okuma-yazma` — aracı, ortak sunucuda arama yapabilir VE bu depodan yeni sayfalar yazabilir
- `sadece okuma` — aracı arama yapabilir ancak asla yazmaz (çoklu müşteri danışmanları için en iyisi: paylaşılan sunucuda arama yapın, Müşteri A'nın çalışmasıyla Müşteri B'nin deposunda kirletmeyin)
- `reddetme` — hiçbir şekilde gbrain etkileşimi yok

Beceri, depo başına bir kez sorar. Karar, aynı uzak sunucunun çalışma ağaçları ve dalları arasında kalıcıdır.

**GStack bellek senkronizasyonu (farklı özellik, aynı özel depo altyapısı).** İsteğe bağlı olarak gstack durumunuzu (öğrenilenler, CEO planları, tasarım belgeleri, retrospektifler, geliştirici profili) özel bir git deposuna gönderir, böylece belleğiniz makineler arasında sizinle birlikte taşınır; tek seferlik gizlilik uyarısı (izin verilen her şey / yalnızca yapılar / kapalı) ve AWS anahtarlarını, token'ları, PEM bloklarını ve JWT'leri makinenizden ayrılmadan önce engelleyen derinlemesine savunma sağlayan bir gizli tarayıcı içerir.

```bash
gstack-brain-init
```

**Gstack'i Conductor'da mı çalıştırıyorsunuz?** Conductor, her çalışma alanının işlem ortamından `ANTHROPIC_API_KEY` ve `OPENAI_API_KEY`'i açıkça kaldırır, bu nedenle ücretli değerlendirmeler ve gbrain yerleştirmeleri varsayılan olarak çalışmaz. Bunun yerine, Conductor'ın çalışma alanı ortam yapılandırmasında `GSTACK_ANTHROPIC_API_KEY` ve `GSTACK_OPENAI_API_KEY` değişkenlerini ayarlayın; gstack'in TS giriş noktaları bunları çalışma zamanında kanonik adlara dönüştürür. Yeni giriş noktalarına içe aktarmayı eklemek için tüm ayrıntılar ve katkıda bulunanlar kontrol listesi: [Conductor + GSTACK_* ortam değişkenleri](USING_GBRAIN_WITH_GSTACK.md#conductor--gstack_-env-vars).

**Tam kapsamlı bilgi — her senaryo, her bayrak, her yardımcı komut, her sorun giderme adımı:** [USING_GBRAIN_WITH_GSTACK.md](USING_GBRAIN_WITH_GSTACK.md)

Diğer referanslar: [docs/gbrain-sync.md](docs/gbrain-sync.md) (senkronizasyona özel kılavuz) • [docs/gbrain-sync-errors.md](docs/gbrain-sync-errors.md) (hata dizini)

## Belgeler

| Belge | Neleri kapsar |

|-----|---------------|

| [Beceri Derinlemesine İncelemeleri](docs/skills.md) | Her beceri için felsefe, örnekler ve iş akışı (Greptile entegrasyonunu içerir) |

| [Yapımcı Etiği](ETHOS.md) | Yapımcı felsefesi: Gölü Kaynat, İnşa Etmeden Önce Ara, üç bilgi katmanı |

| [GBrain'i GStack ile Kullanma](USING_GBRAIN_WITH_GSTACK.md) | `/setup-gbrain` için her yol, bayrak, ikili yardımcı ve sorun giderme adımı |

| [GBrain Senkronizasyonu](docs/gbrain-sync.md) | Makineler arası bellek kurulumu, gizlilik modları, sorun giderme |

| [Mimari](ARCHITECTURE.md) | Tasarım kararları ve sistem iç yapısı |

| [Tarayıcı Referansı](BROWSER.md) | Tam komut referansı `/browse` için referans |

| [Katkıda Bulunma](CONTRIBUTING.md) | Geliştirme kurulumu, test, katkıda bulunan modu ve geliştirme modu |

| [Değişiklik Günlüğü](CHANGELOG.md) | Her sürümde neler yeni? |

## Gizlilik ve Telemetri

gstack, projeyi geliştirmeye yardımcı olmak için **isteğe bağlı** kullanım telemetrisi içerir. İşte tam olarak neler oluyor:

- **Varsayılan olarak kapalıdır.** Açıkça evet demediğiniz sürece hiçbir şey hiçbir yere gönderilmez.

- **İlk çalıştırmada,** gstack anonim kullanım verilerini paylaşmak isteyip istemediğinizi sorar. Hayır diyebilirsiniz.

- **Gönderilenler (eğer seçerseniz):** beceri adı, süre, başarı/başarısızlık, gstack sürümü, işletim sistemi. Hepsi bu.

- **Asla gönderilmeyenler:** kod, dosya yolları, depo adları, dal adları, istemler veya kullanıcı tarafından oluşturulan herhangi bir içerik.

- **İstediğiniz zaman değiştirin:** `gstack-config set telemetry off` komutu her şeyi anında devre dışı bırakır.

Veriler [Supabase](https://supabase.com) (açık kaynaklı Firebase alternatifi) içinde saklanır. Şema [`supabase/migrations/`](supabase/migrations/) dizinindedir — tam olarak neyin toplandığını doğrulayabilirsiniz. Depodaki Supabase yayınlanabilir anahtarı, bir Firebase API anahtarı gibi genel bir anahtardır — satır düzeyindeki güvenlik politikaları tüm doğrudan erişimi engeller. Telemetri, şema kontrollerini, olay türü izin listelerini ve alan uzunluğu sınırlarını uygulayan doğrulanmış uç fonksiyonlar aracılığıyla akar.

**Yerel analizler her zaman mevcuttur.** Yerel JSONL dosyasından kişisel kullanım panonuzu görmek için `gstack-analytics` komutunu çalıştırın — uzaktan veri gerekmez.

## Sorun Giderme

**Beceri görünmüyor mu?** `cd ~/.claude/skills/gstack && ./setup`

**`/browse` başarısız mı oluyor?** `cd ~/.claude/skills/gstack && bun install && bun run build`

**Kurulum eski mi?** `/gstack-upgrade` komutunu çalıştırın veya `~/.gstack/config.yaml` dosyasında `auto_upgrade: true` ayarını yapın.

**Daha kısa komutlar mı istiyorsunuz?** `cd ~/.claude/skills/gstack && ./setup --no-prefix` — `/gstack-qa`'dan `/qa`'ya geçiş yapar. Seçiminiz gelecekteki yükseltmeler için hatırlanır.

**Adlandırılmış komutlar mı istiyorsunuz?** `cd ~/.claude/skills/gstack && ./setup --prefix` — `/qa` dizinini `/gstack-qa` dizinine değiştirir. Gstack ile birlikte başka beceri paketleri çalıştırıyorsanız kullanışlıdır.

**Codex "Geçersiz SKILL.md nedeniyle beceri(ler) yükleme atlandı" mı diyor?** Codex beceri açıklamalarınız güncel değil. Çözüm: `cd ~/.codex/skills/gstack && git pull && ./setup --host codex` — veya depo yerel kurulumları için: `cd "$(readlink -f .agents/skills/gstack)" && git pull && ./setup --host codex`

**Windows kullanıcıları:** gstack, Git Bash veya WSL aracılığıyla Windows 11'de çalışır. Bun'a ek olarak Node.js gereklidir — Bun'un Windows'ta Playwright'ın pipe transport'uyla ilgili bilinen bir hatası vardır ([bun#4253](https://github.com/oven-sh/bun/issues/4253)). Göz atma sunucusu otomatik olarak Node.js'ye geri döner. Hem `bun` hem de `node`'un PATH'inizde olduğundan emin olun.

Geliştirici Modu olmayan Windows'ta (MSYS2 / Git Bash), `setup`, `ln -snf` komutu `git pull` işleminde yenilenmeyen donmuş kopyalar ürettiği için sembolik bağlantılar yerine dosya kopyalarına geri döner. **Her `git pull` işleminden sonra `cd ~/.claude/skills/gstack && ./setup` komutunu tekrar çalıştırın** böylece beceri dosyalarınız depoyla eşleşir. `setup`, size hatırlatan tek satırlık bir not yazdırır. Unix ve WSL sembolik bağlantıları korur ve tekrar çalıştırmaya gerek duymaz.

**Claude becerileri göremiyor mu diyor?** Projenizin `CLAUDE.md` dosyasında bir gstack bölümü olduğundan emin olun. Şunu ekleyin:

```
## gstack
Tüm web tarama işlemleri için gstack'ten /browse komutunu kullanın. Asla mcp__claude-in-chrome__* araçlarını kullanmayın.

Mevcut beceriler: /ofis-saatleri, /CEO-incelemesi-planı, /mühendis-incelemesi-planı, /tasarım-incelemesi-planı,
/tasarım-danışmanlığı, /tasarım-shotgun, /html-tasarım, /inceleme, /gönderme, /yerleştirme ve dağıtım,
/canary, /benchmark, /browse, /gstack-browser-açma, /qa, /qa-sadece, /tasarım-incelemesi,
/tarayıcı-çerezleri-kurulum, /dağıtım-kurulum, /gbrain-kurulum, /gbrain-senkronizasyon, /retro, /araştırma,

/belge-yayınlama, /belge-oluşturma, /codex, /cso, /otomatik-planlama, /çift-ajan, /dikkatli, /dondurma,
/koruma, /dondurmanınsonlandırılması, /gstack-yükseltme, /öğrenme.

```

## Lisans

MIT. Sonsuza dek ücretsiz. Gidip bir şeyler inşa edin.
### Adım 2: Ekip modu — paylaşılan depolar için otomatik güncelleme (önerilir)

Deponuzun içinden bunu yapıştırın. Sizi ekip moduna geçirir, depoyu başlatır, böylece ekip arkadaşları da kullanabilir.
