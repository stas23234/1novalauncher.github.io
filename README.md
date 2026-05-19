[deepseek_javascript_20260519_9218a2 (1).js](https://github.com/user-attachments/files/28024872/deepseek_javascript_20260519_9218a2.1.js)
// Плавная прокрутка
document.querySelectorAll('.nav-links a, .btn[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function(e) {
        const targetId = this.getAttribute('href');
        if (targetId && targetId.startsWith('#')) {
            e.preventDefault();
            const targetElement = document.querySelector(targetId);
            if (targetElement) {
                targetElement.scrollIntoView({ behavior: 'smooth', block: 'start' });
            }
        }
    });
});

// Кнопка скачивания
const downloadBtn = document.getElementById('downloadBtn');
if (downloadBtn) {
    downloadBtn.addEventListener('click', function() {
        setTimeout(() => {
            const msg = document.createElement('div');
            msg.innerHTML = '<i class="fas fa-info-circle"></i> Загрузка началась! Файл сохранится в папку "Загрузки".';
            msg.style.cssText = 'position:fixed;bottom:20px;left:50%;transform:translateX(-50%);background:#1f2a4e;color:#ffec99;padding:12px 24px;border-radius:40px;z-index:9999;font-weight:bold;backdrop-filter:blur(12px);border:1px solid #ffcc77;';
            document.body.appendChild(msg);
            setTimeout(() => msg.remove(), 5000);
        }, 100);
    });
}

// Discord кнопка
const discordBtn = document.getElementById('discordBtn');
if (discordBtn) {
    discordBtn.addEventListener('click', (e) => {
        e.preventDefault();
        alert('⚡ Discord сервер: https://discord.gg/novalauncher\n(замените на реальную ссылку)');
    });
}

// Анимация появления
const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            entry.target.style.opacity = '1';
            entry.target.style.transform = 'translateY(0)';
            observer.unobserve(entry.target);
        }
    });
}, { threshold: 0.1 });

document.querySelectorAll('.feature-card, .download-zone, .help-content, .community-section').forEach(el => {
    el.style.opacity = '0';
    el.style.transform = 'translateY(20px)';
    el.style.transition = 'opacity 0.5s, transform 0.5s';
    observer.observe(el);
});

console.log('✅ NOVA Launcher сайт загружен!');
