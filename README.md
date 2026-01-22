index.html  <div class="grid" id="diarios"></div>

  <h2>🔵 Planos Semanais (7 dias)</h2>
  <div class="grid" id="semanais"></div>

  <h2>🔴 Planos Mensais (30 dias)</h2>
  <div class="grid" id="mensais"></div>

  <div class="payments">
    <h2>💳 Formas de Pagamento</h2>
    <div class="pay">M‑Pesa: <b id="mpesa">850714233</b> <button class="copy-btn" onclick="copyText('850714233')">Copiar</button></div>
    <div class="pay">E‑Mola: <b id="emola">861731475</b> <button class="copy-btn" onclick="copyText('861731475')">Copiar</button></div>
    <p class="info">Envie o comprovativo + número</p>
  </div>

</div>

<a class="whatsapp" href="https://wa.me/258850714233?text=Posso%20comprar%20megas%3F" target="_blank">
  <i class="fab fa-whatsapp"></i> Comprar
</a>

<footer>
  Criado por Daúdo OmarJr • D‑Connect © 2025
</footer>

<script>
  const diarios = [
    ['512MB','10MT'],['1GB','16MT'],['2GB','32MT'],['3GB','48MT'],['4GB','64MT'],['5GB','80MT'],['6GB','96MT'],['7GB','112MT'],['8GB','128MT'],['9GB','144MT'],['10GB','160MT']
  ];
  const semanais = [
    ['1.5GB','60MT'],['2.5GB','110MT'],['4.5GB','160MT'],['6.8GB','215MT'],['10GB','320MT']
  ];
  const mensais = [
    ['10GB','270MT'],['18GB','398MT'],['28GB','526MT'],['30GB','654MT']
  ];

  function render(list, id){
    const el = document.getElementById(id);
    list.forEach(p=>{
      const d = document.createElement('div');
      d.className='card';
      d.innerHTML = `<span>${p[0]}</span><strong>${p[1]}</strong>`;
      d.onclick = ()=>{
        if(confirm(`Deseja comprar ${p[0]} por ${p[1]}?`)){
          window.open('https://wa.me/258850714233?text=Posso%20comprar%20megas%3F','_blank');
        }
      };
      el.appendChild(d);
    });
  }

  render(diarios,'diarios');
  render(semanais,'semanais');
  render(mensais,'mensais');

  function copyText(text){
    // Clipboard API pode ser bloqueada em ambientes sandbox
    if(navigator.clipboard && window.isSecureContext){
      navigator.clipboard.writeText(text).catch(()=>fallbackCopy(text));
    } else {
      fallbackCopy(text);
    }
  }

  function fallbackCopy(text){
    const temp = document.createElement('textarea');
    temp.value = text;
    document.body.appendChild(temp);
    temp.select();
    try{
      document.execCommand('copy');
      alert('Copiado: ' + text);
    }catch(e){
      alert('Copie manualmente: ' + text);
    }
    document.body.removeChild(temp);
  }
</script>

</body>
</html>
