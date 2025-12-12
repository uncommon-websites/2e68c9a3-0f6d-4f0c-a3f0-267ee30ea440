<script>
  import { onMount } from 'svelte';

  let isScrolled = false;

  onMount(() => {
    const handleScroll = () => {
      isScrolled = window.scrollY > 10;
    };
    window.addEventListener('scroll', handleScroll);
    return () => window.removeEventListener('scroll', handleScroll);
  });
</script>

<header class="fixed top-0 left-0 right-0 z-50 transition-all duration-300 px-6 py-5 flex items-center justify-between {isScrolled ? 'bg-[#F9F8F6]/90 backdrop-blur-md shadow-sm' : 'bg-transparent'}">
  <div class="flex items-center">
    <!-- Logo -->
    <a href="/" class="flex items-center gap-3 group">
      <svg width="40" height="25" viewBox="0 0 102 64" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" clip-rule="evenodd" d="M0.464844 36.6203C20.766 36.6203 37.2233 20.2248 37.2233 0H64.7063C64.7063 20.2248 81.1637 36.6203 101.465 36.6203V64C80.9762 64 62.7279 54.4446 50.9648 39.563C39.2018 54.4446 20.9534 64 0.464844 64V36.6203Z" fill="black"/>
      </svg>
      <span class="font-semibold text-base text-[#1A1A1A] leading-tight">Centrum Opieki<br/>Medycznej</span>
    </a>
  </div>

  <div class="flex items-center gap-8">
    <nav class="hidden md:flex items-center gap-8 text-[13px] font-medium text-gray-600">
      <a href="#uslugi" class="hover:text-black transition-colors">Usługi</a>
      <a href="#lekarze" class="hover:text-black transition-colors">Lekarze</a>
      <a href="#kontakt" class="hover:text-black transition-colors">Kontakt</a>
    </nav>
    <a href="#kontakt" class="bg-[#1A1A1A] text-white text-[13px] font-medium px-5 py-2.5 rounded-sm hover:bg-black transition-colors">
      Umów wizytę
    </a>
  </div>
</header>