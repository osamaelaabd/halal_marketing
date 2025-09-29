<!doctype html>
<html lang="ar" dir="rtl">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>البيع الحلال العالمي - منصة التجارة الذكية</title>
    
    <!-- PWA Meta Tags -->
    <meta name="theme-color" content="#10b981" />
    <meta name="description" content="منصة التجارة العالمية الذكية - عمولة 1% فقط - توصيل مباشر - ذكاء اصطناعي" />
    
    <!-- Apple PWA Meta Tags -->
    <meta name="apple-mobile-web-app-capable" content="yes" />
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent" />
    <meta name="apple-mobile-web-app-title" content="البيع الحلال العالمي" />
    
    <!-- Icons -->
    <link rel="apple-touch-icon" href="/icon-192x192.png" />
    <link rel="icon" type="image/png" sizes="192x192" href="/icon-192x192.png" />
    <link rel="icon" type="image/png" sizes="512x512" href="/icon-512x512.png" />
    
    <!-- Manifest -->
    <link rel="manifest" href="/manifest.json" />
    
    <!-- Microsoft Tiles -->
    <meta name="msapplication-TileColor" content="#10b981" />
    <meta name="msapplication-TileImage" content="/icon-192x192.png" />
    
    <script>
      // Register Service Worker
      if ('serviceWorker' in navigator) {
        window.addEventListener('load', function() {
          navigator.serviceWorker.register('/sw.js')
            .then(function(registration) {
              console.log('SW registered: ', registration);
            }, function(registrationError) {
              console.log('SW registration failed: ', registrationError);
            });
        });
      }
      
      // PWA Install Prompt
      let deferredPrompt;
      let installButton = null;
      
      window.addEventListener('beforeinstallprompt', (e) => {
        console.log('beforeinstallprompt fired');
        e.preventDefault();
        deferredPrompt = e;
        
        // Show install button
        if (installButton) {
          installButton.style.display = 'block';
        }
        
        // Create floating install button if not exists
        if (!document.getElementById('floating-install-btn')) {
          createFloatingInstallButton();
        }
      });
      
      function createFloatingInstallButton() {
        const floatingBtn = document.createElement('div');
        floatingBtn.id = 'floating-install-btn';
        floatingBtn.innerHTML = `
          <div style="
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: linear-gradient(45deg, #10b981, #059669);
            color: white;
            padding: 12px 16px;
            border-radius: 50px;
            box-shadow: 0 4px 12px rgba(16, 185, 129, 0.4);
            cursor: pointer;
            z-index: 1000;
            font-size: 14px;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 8px;
            animation: bounce 2s infinite;
            max-width: 200px;
          ">
            📱 ثبت التطبيق
          </div>
          <style>
            @keyframes bounce {
              0%, 20%, 50%, 80%, 100% { transform: translateY(0); }
              40% { transform: translateY(-10px); }
              60% { transform: translateY(-5px); }
            }
          </style>
        `;
        
        floatingBtn.addEventListener('click', installApp);
        document.body.appendChild(floatingBtn);
      }
      
      function installApp() {
        if (deferredPrompt) {
          deferredPrompt.prompt();
          deferredPrompt.userChoice.then((choiceResult) => {
            if (choiceResult.outcome === 'accepted') {
              console.log('User accepted the install prompt');
              // Hide install button
              const floatingBtn = document.getElementById('floating-install-btn');
              if (floatingBtn) {
                floatingBtn.style.display = 'none';
              }
            }
            deferredPrompt = null;
          });
        } else {
          // Fallback for iOS or other browsers
          alert('لتثبيت التطبيق:\n\n1. اضغط على زر المشاركة في المتصفح\n2. اختر "إضافة إلى الشاشة الرئيسية"\n3. اضغط "إضافة"');
        }
      }
      
      // Make install function global
      window.installApp = installApp;
      
      // Check if app is already installed
      window.addEventListener('appinstalled', (evt) => {
        console.log('App was installed');
        const floatingBtn = document.getElementById('floating-install-btn');
        if (floatingBtn) {
          floatingBtn.style.display = 'none';
        }
      });
    </script>
    <script type="module" crossorigin src="/assets/index-dEbuIznu.js"></script>
    <link rel="stylesheet" crossorigin href="/assets/index-KNspsIzE.css">
  </head>
  <body>
    <div id="root"></div>
  <script src="https://public-frontend-cos.metadl.com/commonfile/appPlugins-prod-1757257819217.js" crossorigin="anonymous" referrerpolicy="no-referrer"></script></body>
</html>
