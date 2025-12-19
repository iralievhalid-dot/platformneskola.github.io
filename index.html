<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>Platform 2025 | Control</title>
    <script src="https://unpkg.com/@supabase/supabase-js@2"></script>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-100 flex items-center justify-center min-h-screen font-sans">

    <div id="login-form" class="bg-white p-8 rounded-2xl shadow-xl w-full max-w-sm border border-gray-200">
        <h2 class="text-2xl font-black mb-6 text-center text-gray-800">ВХОД В СИСТЕМУ</h2>
        <input type="text" id="uname" placeholder="Логин (из Supabase)" class="w-full p-3 mb-3 border rounded-xl focus:ring-2 focus:ring-blue-500 outline-none">
        <input type="password" id="pass" placeholder="Пароль" class="w-full p-3 mb-6 border rounded-xl focus:ring-2 focus:ring-blue-500 outline-none">
        <button onclick="login()" id="btn" class="w-full bg-blue-600 text-white font-bold py-3 rounded-xl hover:bg-blue-700 transition-all">ВОЙТИ</button>
        <p id="msg" class="text-red-500 text-sm mt-4 text-center hidden"></p>
    </div>

    <div id="content" class="hidden w-full max-w-4xl p-6">
        <div class="bg-white p-10 rounded-3xl shadow-2xl text-center">
            <h1 class="text-4xl font-black mb-4">ДОБРО ПОЖАЛОВАТЬ!</h1>
            <p id="welcome-text" class="text-xl text-gray-600 mb-8"></p>
            <div class="p-6 bg-green-50 border-2 border-dashed border-green-200 rounded-2xl">
                <p class="text-green-700 font-bold">Связь с базой данных подтверждена.</p>
                <p class="text-green-600 text-sm">Ты авторизован как Хранитель/Учитель.</p>
            </div>
            <button onclick="location.reload()" class="mt-8 text-gray-400 hover:text-red-500 underline text-sm">Выйти из системы</button>
        </div>
    </div>

    <script>
        const S_URL = "https://ihwxjkqzjaacizarwugc.supabase.co";
        const S_KEY = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Imlod3hqa3F6amFhY2l6YXJ3dWdjIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjYxNTEzNzcsImV4cCI6MjA4MTcyNzM3N30.wP8r-0PoBtF8pgP1cv_nSW4ueHPnRSeLQtdv9nA8Vu0";
        const _supabase = supabase.createClient(S_URL, S_KEY);

        async function login() {
            const u = document.getElementById('uname').value;
            const p = document.getElementById('pass').value;
            const btn = document.getElementById('btn');
            const msg = document.getElementById('msg');

            btn.innerText = "ПРОВЕРКА...";
            msg.classList.add('hidden');

            try {
                const { data, error } = await _supabase
                    .from('users')
                    .select('*')
                    .eq('username', u)
                    .eq('password', p)
                    .single();

                if (error || !data) throw new Error("Неверный логин или пароль");

                // Прячем вход, показываем успех
                document.getElementById('login-form').classList.add('hidden');
                document.getElementById('content').classList.remove('hidden');
                document.getElementById('welcome-text').innerText = `Привет, ${data.first_name}! Твоя роль: ${data.role}`;

            } catch (err) {
                msg.innerText = err.message;
                msg.classList.remove('hidden');
                btn.innerText = "ВОЙТИ";
            }
        }
    </script>
</body>
</html>
