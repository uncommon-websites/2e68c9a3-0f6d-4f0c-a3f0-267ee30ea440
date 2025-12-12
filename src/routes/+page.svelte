<script lang="ts">
  import Header from "$lib/components/Header.svelte";
  
  // Icons
  const ArrowRight = `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>`;
  const PlayCircle = `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><polygon points="10 8 16 12 10 16 10 8"/></svg>`;
  const ChevronLeft = `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m15 18-6-6 6-6"/></svg>`;
  const ChevronRight = `<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m9 18 6-6-6-6"/></svg>`;
  const Check = `<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round"><path d="M20 6 9 17l-5-5"/></svg>`;
  const Plus = `<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14"/><path d="M12 5v14"/></svg>`;
  const Instagram = `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="20" height="20" x="2" y="2" rx="5" ry="5"/><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"/><line x1="17.5" x2="17.51" y1="6.5" y2="6.5"/></svg>`;
  const LinkedIn = `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect width="4" height="12" x="2" y="9"/><circle cx="4" cy="4" r="2"/></svg>`;
  const XIcon = `<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 6 6 18"/><path d="m6 6 18 12"/></svg>`;

  // Data
  const heroImages = [
    "/generated/image-female-doctor-in-white-coat-consulting-w-1765531945253-0.webp",
    "/generated/image-male-doctor-examining-patients-blood-pre-1765531948558-1.webp",
    "/generated/image-clean-modern-medical-clinic-waiting-room-1765531950711-2.webp",
    "/generated/image-doctor-reviewing-medical-charts-with-mid-1765531952859-3.webp",
    "/generated/image-medical-professional-conducting-health-s-1765531955029-4.webp",
    "/generated/image-friendly-doctor-with-stethoscope-smiling-1765531957214-5.webp"
  ];

  const benefitCards = [
    {
      title: "Medycyna Rodzinna",
      desc: "Kompleksowa opieka zdrowotna dla całej rodziny. Doświadczeni specjaliści zapewniają profesjonalną diagnostykę i leczenie.",
      image: "/generated/image-doctor-listening-to-patients-heart-with--1765531963705-8.webp"
    },
    {
      title: "Medycyna Pracy",
      desc: "Badania profilaktyczne pracowników. Współpracujemy z wiodącymi ubezpieczycielami zdrowotnymi. Badania tego samego dnia.",
      image: "/generated/image-occupational-health-doctor-conducting-wo-1765531965837-9.webp"
    },
    {
      title: "Opieka Profilaktyczna",
      desc: "Programy profilaktyczne i specjalistyczne uprawnienia do badań pracowników narażonych na promieniowanie jonizujące.",
      image: "/generated/image-doctor-reviewing-preventive-health-scree-1765531968037-10.webp"
    }
  ];

  const steps = [
    {
      step: 1,
      title: "Rejestracja pacjenta",
      desc: "Zarejestruj się w naszej przychodni osobiście lub telefonicznie. Przyjmujemy pacjentów NFZ oraz prywatnie.",
      image: "plan"
    },
    {
      step: 2,
      title: "Umów wizytę",
      desc: "Wybierz dogodny termin wizyty. Medycyna pracy dostępna codziennie po godzinie 12:00.",
      image: "schedule"
    },
    {
      step: 3,
      title: "Konsultacja lekarska",
      desc: "Spotkanie z doświadczonym specjalistą medycyny rodzinnej lub medycyny pracy. Dokładne badanie i diagnostyka.",
      image: "results"
    },
    {
      step: 4,
      title: "Badania i dokumentacja",
      desc: "W razie potrzeby zlecamy dodatkowe badania. Wystawiamy orzeczenia lekarskie i zaświadczenia.",
      image: "notes"
    },
    {
      step: 5,
      title: "Opieka długoterminowa",
      desc: "Kontynuuj opiekę zdrowotną w naszej przychodni. Regularny monitoring stanu zdrowia i profilaktyka.",
      image: "improve"
    }
  ];

  const faqs = [
    "Jakie są godziny przyjęć w przychodni?",
    "Czy przyjmujecie pacjentów NFZ?",
    "Jakie ubezpieczenia prywatne są akceptowane?",
    "Czy badania medycyny pracy można wykonać tego samego dnia?",
    "Jakie specjalistyczne uprawnienia posiada przychodnia?",
    "Czy dermatolog nadal przyjmuje w Piszu?"
  ];
</script>

<Header />

<main class="w-full overflow-x-hidden">
  <!-- Hero Section -->
  <section class="pt-32 pb-16 md:pt-40 md:pb-24 px-6 text-center max-w-7xl mx-auto">
    <h1 class="text-4xl md:text-6xl lg:text-7xl font-medium tracking-tight text-[#1A1A1A] mb-6 leading-[1.1]">
      Kompleksowa opieka<br />zdrowotna w Piszu
    </h1>
    <p class="text-gray-600 text-lg md:text-xl max-w-3xl mx-auto mb-10 leading-relaxed font-light">
      Medycyna rodzinna i medycyna pracy. Doświadczeni specjaliści, programy profilaktyczne i współpraca z wiodącymi ubezpieczycielami zdrowotnymi.
    </p>
    <a href="#kontakt" class="inline-block bg-[#1A1A1A] text-white px-8 py-3.5 rounded-sm font-medium hover:bg-black transition-colors">
      Umów wizytę
    </a>
  </section>

  <!-- Hero Images Scroll -->
  <div class="w-full overflow-x-auto pb-12 hide-scrollbar">
    <div class="flex gap-4 px-6 min-w-max">
      {#each heroImages as img, i}
        <div class="relative w-48 h-64 md:w-64 md:h-80 rounded-3xl overflow-hidden flex-shrink-0">
          <img src={img} alt="Lifestyle" class="w-full h-full object-cover" />
        </div>
      {/each}
    </div>
  </div>

  <!-- Doctors Section -->
  <section class="py-20 px-6 max-w-7xl mx-auto" id="lekarze">
    <div class="text-center mb-16">
      <h2 class="text-3xl md:text-4xl font-medium mb-4">Nasi lekarze</h2>
      <p class="text-gray-600 font-light max-w-2xl mx-auto">Doświadczeni specjaliści z podwójnymi specjalizacjami w medycynie rodzinnej i medycynie pracy.</p>
    </div>

    <div class="grid md:grid-cols-2 gap-8">
      <!-- Doctor 1: Ewa Chodnicka -->
      <div class="bg-white rounded-[32px] overflow-hidden shadow-sm">
        <div class="aspect-[3/4] overflow-hidden">
          <img src="/generated/image-professional-female-doctor-in-her-40s-wi-1765531959369-6.webp" alt="Ewa Chodnicka" class="w-full h-full object-cover" />
        </div>
        <div class="p-8">
          <h3 class="text-2xl font-medium mb-2">Ewa Chodnicka</h3>
          <p class="text-gray-600 mb-4">Specjalista Medycyny Rodzinnej i Medycyny Pracy</p>
          <p class="text-sm text-gray-500 font-light leading-relaxed">
            Właścicielka przychodni z wieloletnim doświadczeniem w kompleksowej opiece zdrowotnej nad pacjentami i pracownikami.
          </p>
        </div>
      </div>

      <!-- Doctor 2: Paweł Zdziechowski -->
      <div class="bg-white rounded-[32px] overflow-hidden shadow-sm">
        <div class="aspect-[3/4] overflow-hidden">
          <img src="/generated/image-professional-male-doctor-in-his-40s-with-1765531961564-7.webp" alt="Paweł Zdziechowski" class="w-full h-full object-cover" />
        </div>
        <div class="p-8">
          <h3 class="text-2xl font-medium mb-2">Paweł Zdziechowski</h3>
          <p class="text-gray-600 mb-4">Specjalista Chorób Wewnętrznych i Medycyny Pracy</p>
          <p class="text-sm text-gray-500 font-light leading-relaxed">
            Były właściciel NZPOZ Rodzinna Przychodnia Zdrowia, specjalista w zintegrowanej opiece nad pacjentem.
          </p>
        </div>
      </div>
    </div>
  </section>

  <!-- Value Proposition -->
  <section class="py-16 px-6 max-w-7xl mx-auto">
    <div class="grid md:grid-cols-2 gap-12 items-start">
      <h2 class="text-3xl md:text-5xl font-medium tracking-tight text-[#1A1A1A] leading-tight">
        Twoje zdrowie w dobrych rękach
      </h2>
      <p class="text-gray-600 text-lg font-light leading-relaxed">
        Zapewniamy kompleksową opiekę zdrowotną dla mieszkańców Pisza. Doświadczeni specjaliści, nowoczesny sprzęt i indywidualne podejście do każdego pacjenta. Współpracujemy z NFZ oraz wiodącymi prywatnymi ubezpieczycielami zdrowotnymi.
      </p>
    </div>
  </section>

  <!-- Benefit Cards -->
  <section class="py-8 px-6 max-w-7xl mx-auto">
    <div class="grid md:grid-cols-3 gap-6">
      {#each benefitCards as card}
        <div class="relative h-[480px] rounded-3xl overflow-hidden group">
          <img src={card.image} alt={card.title} class="absolute inset-0 w-full h-full object-cover transition-transform duration-700 group-hover:scale-105" />
          <div class="absolute inset-0 bg-gradient-to-t from-black/60 via-black/20 to-transparent"></div>
          <div class="absolute bottom-0 left-0 right-0 p-8 text-white">
            <h3 class="text-2xl font-medium mb-3">{card.title}</h3>
            <p class="text-white/80 text-sm leading-relaxed font-light">{card.desc}</p>
          </div>
        </div>
      {/each}
    </div>
  </section>

  <!-- Testimonial -->
  <section class="py-24 px-6 max-w-4xl mx-auto text-center">
    <blockquote class="text-2xl md:text-3xl font-medium leading-relaxed text-[#1A1A1A] mb-8">
      "Centrum Opieki Medycznej to przychodnia, której mogę zaufać. Lekarze są kompetentni, zawsze mają czas na wysłuchanie pacjenta. Czuję się tu bezpiecznie i wiem, że moje zdrowie jest w dobrych rękach."
    </blockquote>
    <div class="flex flex-col items-center gap-3">
      <img src="/generated/image-satisfied-elderly-patient-smiling-after--1765531970214-11.webp" alt="Pacjent" class="w-16 h-16 rounded-full object-cover" />
      <div class="text-center">
        <div class="font-medium text-sm">Maria K.</div>
        <div class="text-gray-500 text-xs">Pacjentka przychodni</div>
      </div>
    </div>
  </section>

  <!-- Stats Grid -->
  <section class="py-12 px-6 max-w-7xl mx-auto border-t border-gray-200">
    <div class="grid md:grid-cols-3 gap-8 text-center md:text-left">
      <div>
        <h3 class="text-xl font-medium mb-2">Badania tego samego dnia</h3>
        <p class="text-gray-500 text-sm font-light">Medycyna pracy dostępna codziennie po godzinie 12:00. Szybko i profesjonalnie.</p>
      </div>
      <div>
        <h3 class="text-xl font-medium mb-2">5 ubezpieczycieli prywatnych</h3>
        <p class="text-gray-500 text-sm font-light">Współpracujemy z Luxmed, Medicover, Enelmed, PZU Zdrowie i Świat Zdrowia.</p>
      </div>
      <div>
        <h3 class="text-xl font-medium mb-2">Specjalistyczne uprawnienia</h3>
        <p class="text-gray-500 text-sm font-light">Badania pracowników narażonych na promieniowanie jonizujące, żeglugi śródlądowej i kierowców zawodowych.</p>
      </div>
    </div>
  </section>

  <!-- How it works -->
  <section class="py-20 px-6 max-w-7xl mx-auto">
    <div class="mb-16 max-w-md">
      <h2 class="text-4xl font-medium mb-6">Jak to działa</h2>
      <p class="text-gray-600 font-light">Proces rejestracji i opieki zdrowotnej w naszej przychodni jest prosty i przejrzysty. Od pierwszej wizyty po długoterminową opiekę - jesteśmy z Tobą na każdym etapie.</p>
    </div>

    <div class="space-y-6">
      {#each steps as step}
        <div class="bg-white rounded-[40px] p-8 md:p-12 flex flex-col items-center text-center max-w-2xl mx-auto shadow-sm">
          <div class="w-full text-left mb-8">
            <span class="inline-block w-8 h-8 rounded-full border border-gray-200 text-center leading-8 text-sm font-medium mb-4">{step.step}</span>
            <h3 class="text-2xl font-medium mb-3">{step.title}</h3>
            <p class="text-gray-500 font-light text-sm max-w-lg">{step.desc}</p>
          </div>
          
          <!-- Phone Mockup for Step -->
          <div class="relative w-[240px] h-[480px] bg-black rounded-[35px] border-[6px] border-black shadow-xl overflow-hidden mt-4">
             <div class="absolute top-0 left-0 right-0 h-5 bg-black z-20 flex justify-center">
                <div class="w-16 h-3 bg-black rounded-b-lg"></div>
             </div>
             <div class="w-full h-full bg-white pt-8 px-3 overflow-hidden">
                <!-- Dynamic Content based on step -->
                {#if step.image === 'plan'}
                  <div class="space-y-3 mt-4">
                    <div class="p-3 border rounded-xl border-black bg-gray-50">
                      <div class="font-bold text-xs mb-1">Optimal ID</div>
                      <div class="h-1 w-full bg-gray-200 rounded"></div>
                    </div>
                    <div class="p-3 border rounded-xl border-gray-200">
                       <div class="font-bold text-xs mb-1 text-gray-400">Essential</div>
                       <div class="h-1 w-full bg-gray-100 rounded"></div>
                    </div>
                  </div>
                {:else if step.image === 'schedule'}
                   <div class="mt-4">
                     <div class="text-center font-bold mb-4">Appointment</div>
                     <div class="bg-gray-100 h-32 rounded-xl mb-3 flex items-center justify-center text-xs text-gray-400">Map View</div>
                     <button class="w-full bg-black text-white text-xs py-2 rounded-lg">Confirm</button>
                   </div>
                {:else if step.image === 'results'}
                   <div class="bg-black h-full -mx-3 -mt-8 pt-10 px-3 text-white">
                      <div class="text-center mb-6">
                        <div class="w-12 h-12 bg-gray-700 rounded-full mx-auto mb-2"></div>
                        <div class="text-sm font-bold">Grace Parker</div>
                      </div>
                      <div class="space-y-2">
                         <div class="bg-gray-800 p-2 rounded-lg h-10"></div>
                         <div class="bg-gray-800 p-2 rounded-lg h-10"></div>
                      </div>
                   </div>
                {:else if step.image === 'notes'}
                   <div class="mt-4 space-y-3">
                      <div class="font-bold text-sm">Health Status</div>
                      <div class="text-[10px] text-gray-500 leading-relaxed">
                        You usually make smart choices for your health through regular exercise...
                      </div>
                      <div class="bg-gray-50 p-2 rounded text-[10px] text-gray-600">
                        Since your diet lacks enough fruits and vegetables...
                      </div>
                   </div>
                {:else}
                   <div class="mt-4 flex flex-col h-full">
                      <div class="flex-1">
                        <div class="bg-gray-100 p-2 rounded-lg rounded-tl-none text-[10px] mb-2 max-w-[80%]">
                          What benefits can I get by bringing ApoB closer to the optimal range?
                        </div>
                        <div class="bg-blue-50 p-2 rounded-lg rounded-tr-none text-[10px] ml-auto max-w-[80%]">
                          By lowering ApoB, you reduce the number of cholesterol-carrying particles...
                        </div>
                      </div>
                      <div class="h-10 border-t mt-2"></div>
                   </div>
                {/if}
             </div>
          </div>
        </div>
      {/each}
    </div>
  </section>

  <!-- Dark Cards Section -->
  <section class="py-8 px-6 max-w-7xl mx-auto">
    <div class="grid md:grid-cols-2 gap-6">
      <!-- Insurance Partnerships Card -->
      <div class="bg-[#111] rounded-[40px] p-8 md:p-12 text-white min-h-[500px] flex flex-col relative overflow-hidden">
        <div class="relative z-10">
          <h3 class="text-sm font-medium text-gray-400 mb-2">Szeroka współpraca</h3>
          <h2 class="text-2xl md:text-3xl font-medium max-w-xs mb-8">Współpracujemy z NFZ i wiodącymi ubezpieczycielami</h2>
          <div class="space-y-3 text-sm text-gray-300">
            <div class="flex items-center gap-2">
              <div class="w-1.5 h-1.5 rounded-full bg-primary-400"></div>
              <span>NFZ - Narodowy Fundusz Zdrowia</span>
            </div>
            <div class="flex items-center gap-2">
              <div class="w-1.5 h-1.5 rounded-full bg-primary-400"></div>
              <span>Luxmed</span>
            </div>
            <div class="flex items-center gap-2">
              <div class="w-1.5 h-1.5 rounded-full bg-primary-400"></div>
              <span>Medicover</span>
            </div>
            <div class="flex items-center gap-2">
              <div class="w-1.5 h-1.5 rounded-full bg-primary-400"></div>
              <span>Enelmed</span>
            </div>
            <div class="flex items-center gap-2">
              <div class="w-1.5 h-1.5 rounded-full bg-primary-400"></div>
              <span>PZU Zdrowie</span>
            </div>
            <div class="flex items-center gap-2">
              <div class="w-1.5 h-1.5 rounded-full bg-primary-400"></div>
              <span>Świat Zdrowia</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Specialized Certifications Card -->
      <div class="bg-[#111] rounded-[40px] p-8 md:p-12 text-white min-h-[500px] flex flex-col relative overflow-hidden">
        <div class="relative z-10">
          <h3 class="text-sm font-medium text-gray-400 mb-2">Specjalistyczne uprawnienia</h3>
          <h2 class="text-2xl md:text-3xl font-medium max-w-xs mb-8">Unikalne certyfikacje w medycynie pracy</h2>
          <div class="space-y-4 text-sm">
            <div>
              <div class="font-medium text-white mb-1">Promieniowanie jonizujące</div>
              <div class="text-gray-400 text-xs">Badania pracowników narażonych - dentyści, personel szpitalny</div>
            </div>
            <div>
              <div class="font-medium text-white mb-1">Żegluga śródlądowa</div>
              <div class="text-gray-400 text-xs">Wydawanie zaświadczeń dla pracowników żeglugi śródlądowej</div>
            </div>
            <div>
              <div class="font-medium text-white mb-1">Kierowcy zawodowi</div>
              <div class="text-gray-400 text-xs">Orzeczenia zgodnie z Ustawą o Transporcie Drogowym</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- Services Section -->
  <section class="py-24 px-6 max-w-7xl mx-auto" id="uslugi">
    <div class="text-center mb-16">
      <h2 class="text-3xl md:text-4xl font-medium mb-4">Nasze usługi</h2>
      <p class="text-gray-500 font-light max-w-2xl mx-auto">Kompleksowa opieka zdrowotna dla rodzin i firm. Przyjmujemy pacjentów NFZ oraz prywatnie.</p>
    </div>

    <div class="grid md:grid-cols-2 gap-6 max-w-4xl mx-auto">
      <!-- Family Medicine -->
      <div class="bg-white rounded-[32px] p-8 flex flex-col">
        <div class="w-12 h-12 bg-primary-100 rounded-full mb-6 flex items-center justify-center">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-primary-600"><path d="M19 14c1.49-1.46 3-3.21 3-5.5A5.5 5.5 0 0 0 16.5 3c-1.76 0-3 .5-4.5 2-1.5-1.5-2.74-2-4.5-2A5.5 5.5 0 0 0 2 8.5c0 2.3 1.5 4.05 3 5.5l7 7Z"/></svg>
        </div>
        <h3 class="text-2xl font-medium mb-1">Medycyna Rodzinna</h3>
        <p class="text-sm text-gray-500 mb-6">Kompleksowa opieka dla całej rodziny</p>
        <ul class="space-y-4 mb-8 flex-1">
          <li class="flex items-start gap-3 text-sm text-gray-600 font-light">
            <span class="mt-0.5 text-black">{@html Check}</span>
            Konsultacje lekarskie w ramach NFZ
          </li>
          <li class="flex items-start gap-3 text-sm text-gray-600 font-light">
            <span class="mt-0.5 text-black">{@html Check}</span>
            Diagnostyka i leczenie chorób przewlekłych
          </li>
          <li class="flex items-start gap-3 text-sm text-gray-600 font-light">
            <span class="mt-0.5 text-black">{@html Check}</span>
            Programy profilaktyczne i szczepienia
          </li>
          <li class="flex items-start gap-3 text-sm text-gray-600 font-light">
            <span class="mt-0.5 text-black">{@html Check}</span>
            Specjaliści: Ewa Chodnicka, Paweł Zdziechowski
          </li>
        </ul>
        <a href="#kontakt" class="w-full bg-[#1A1A1A] text-white py-3 rounded-sm font-medium hover:bg-black transition-colors text-center">Umów wizytę</a>
      </div>

      <!-- Occupational Medicine -->
      <div class="bg-white rounded-[32px] p-8 flex flex-col relative overflow-hidden">
        <div class="absolute top-0 right-0 bg-primary-50 px-4 py-1 rounded-bl-xl text-xs font-medium text-primary-800">Dla firm</div>
        <div class="w-12 h-12 bg-primary-100 rounded-full mb-6 flex items-center justify-center">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-primary-600"><path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M22 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>
        </div>
        <h3 class="text-2xl font-medium mb-1">Medycyna Pracy</h3>
        <p class="text-sm text-gray-500 mb-6">Badania profilaktyczne pracowników</p>
        <ul class="space-y-4 mb-8 flex-1">
          <li class="flex items-start gap-3 text-sm text-gray-600 font-light">
            <span class="mt-0.5 text-black">{@html Check}</span>
            Badania tego samego dnia (po godz. 12:00)
          </li>
          <li class="flex items-start gap-3 text-sm text-gray-600 font-light">
            <span class="mt-0.5 text-black">{@html Check}</span>
            Współpraca z 5 prywatnymi ubezpieczycielami
          </li>
          <li class="flex items-start gap-3 text-sm text-gray-600 font-light">
            <span class="mt-0.5 text-black">{@html Check}</span>
            Specjalistyczne uprawnienia (promieniowanie, żegluga, kierowcy)
          </li>
          <li class="flex items-start gap-3 text-sm text-gray-600 font-light">
            <span class="mt-0.5 text-black">{@html Check}</span>
            Orzeczenia i zaświadczenia lekarskie
          </li>
        </ul>
        <a href="#kontakt" class="w-full bg-[#1A1A1A] text-white py-3 rounded-sm font-medium hover:bg-black transition-colors text-center">Zapytaj o ofertę</a>
      </div>
    </div>
  </section>

  <!-- FAQ -->
  <section class="py-20 px-6 max-w-3xl mx-auto" id="faq">
    <h2 class="text-3xl font-medium text-center mb-12">Najczęściej zadawane pytania</h2>
    <div class="space-y-4">
      {#each faqs as question}
        <div class="border-b border-gray-200 py-4 flex justify-between items-center cursor-pointer group hover:bg-gray-50/50 transition-colors px-2">
          <span class="text-sm md:text-base font-medium text-gray-800">{question}</span>
          <span class="text-gray-400 group-hover:text-black transition-colors">{@html Plus}</span>
        </div>
      {/each}
    </div>
    <div class="mt-12 text-center">
      <a href="#kontakt" class="inline-block border border-gray-300 px-6 py-3 rounded-sm text-xs font-medium hover:bg-gray-50 transition-colors">
        Skontaktuj się z nami
      </a>
    </div>
  </section>

  <!-- Footer -->
  <footer class="py-16 px-6 border-t border-gray-200 bg-[#F9F8F6]" id="kontakt">
    <div class="max-w-7xl mx-auto">
      <div class="grid md:grid-cols-3 gap-12 mb-12">
        <!-- Logo and Description -->
        <div>
          <div class="flex items-center gap-3 mb-4">
            <svg width="40" height="25" viewBox="0 0 102 64" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path fill-rule="evenodd" clip-rule="evenodd" d="M0.464844 36.6203C20.766 36.6203 37.2233 20.2248 37.2233 0H64.7063C64.7063 20.2248 81.1637 36.6203 101.465 36.6203V64C80.9762 64 62.7279 54.4446 50.9648 39.563C39.2018 54.4446 20.9534 64 0.464844 64V36.6203Z" fill="black"/>
            </svg>
            <span class="font-semibold text-base text-[#1A1A1A] leading-tight">Centrum Opieki<br/>Medycznej</span>
          </div>
          <p class="text-sm text-gray-600 font-light">Kompleksowa opieka zdrowotna dla rodzin i firm w Piszu.</p>
        </div>

        <!-- Contact Info -->
        <div>
          <h3 class="font-medium mb-4 text-sm">Kontakt</h3>
          <div class="space-y-2 text-sm text-gray-600 font-light">
            <p>Pisz, Polska</p>
            <p>Tel: <a href="tel:+48" class="hover:text-black">+48 XXX XXX XXX</a></p>
            <p>Email: <a href="mailto:kontakt@com-pisz.pl" class="hover:text-black">kontakt@com-pisz.pl</a></p>
          </div>
          <div class="mt-4 text-xs text-gray-500">
            <p class="font-medium mb-1">Godziny przyjęć:</p>
            <p>Medycyna pracy: codziennie po 12:00</p>
          </div>
        </div>

        <!-- Quick Links -->
        <div>
          <h3 class="font-medium mb-4 text-sm">Szybkie linki</h3>
          <nav class="flex flex-col gap-2 text-sm font-light text-gray-600">
            <a href="#uslugi" class="hover:text-black">Usługi</a>
            <a href="#lekarze" class="hover:text-black">Nasi lekarze</a>
            <a href="#faq" class="hover:text-black">FAQ</a>
            <a href="#kontakt" class="hover:text-black">Kontakt</a>
          </nav>
        </div>
      </div>

      <div class="border-t border-gray-200 pt-8">
        <div class="flex flex-col md:flex-row justify-between items-center gap-4">
          <p class="text-xs text-gray-400">© 2024 Centrum Opieki Medycznej Ewa Chodnicka. Wszelkie prawa zastrzeżone.</p>
          <div class="flex gap-6 text-xs text-gray-400">
            <a href="#" class="hover:text-black">Polityka prywatności</a>
            <a href="#" class="hover:text-black">Regulamin</a>
          </div>
        </div>
      </div>
    </div>
  </footer>
</main>

<style>
  :global(body) {
    background-color: #F9F8F6;
    font-family: 'Inter', sans-serif;
  }
  
  .hide-scrollbar::-webkit-scrollbar {
    display: none;
  }
  .hide-scrollbar {
    -ms-overflow-style: none;
    scrollbar-width: none;
  }
</style>

