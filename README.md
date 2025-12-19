<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Platform 2025 | Admin</title>
    <script src="https://unpkg.com/@supabase/supabase-js@2"></script>
    <script src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-gray-50">
    <div id="root"></div>

    <script type="text/babel">
        const { useState } = React;

        // ТВОИ ДАННЫЕ (ПРОВЕРЬ ИХ)
        const S_URL = "https://ihwxjkqzjaacizarwugc.supabase.co";
        const S_KEY = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Imlod3hqa3F6amFhY2l6YXJ3dWdjIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjYxNTEzNzcsImV4cCI6MjA4MTcyNzM3N30.wP8r-0PoBtF8pgP1cv_nSW4ueHPnRSeLQtdv9nA8Vu0";
        
        // Исправленная инициализация
        const _supabase = window.supabase.createClient(S_URL, S_KEY);

        function App() {
            const [user, setUser] = useState(null);
            const [loading, setLoading] = useState(false);

            const handleLogin = async (e) => {
                e.preventDefault();
                setLoading(true);
                const fd = new FormData(e.target);
                
                try {
                    const { data, error } = await _supabase
                        .from('users')
                        .select('*')
                        .eq('username', fd.get('username'))
                        .eq('password', fd.get('password'))
                        .single();

                    if (error) throw error;
                    if (data) setUser(data);
                } catch (err) {
                    alert("Ошибка входа: " + err.message);
                } finally {
                    setLoading(false);
                }
            };

            if (!user) {
                return (
                    <div className="flex items-center justify-center min-h-screen">
                        <form onSubmit={handleLogin} className="bg-white p-8 rounded-lg shadow-md w-full max-w-sm border">
                            <h2 className="text-xl font-bold mb-4 text-center">Вход для Хранителя и Учителей</h2>
                            <input name="username" placeholder="Логин" className="w-full p-2 mb-3 border rounded" required />
                            <input name="password" type="password" placeholder="Пароль" className="w-full p-2 mb-4 border rounded" required />
                            <button className="w-full bg-blue-500 text-white py-2 rounded hover:bg-blue-600">
                                {loading ? "Связь с базой..." : "Войти"}
                            </button>
                        </form>
                    </div>
                );
            }

            return (
                <div className="p-5">
                    <h1 className="text-2xl font-bold">Добро пожаловать, {user.first_name}!</h1>
                    <p className="text-gray-600">Твоя роль в системе: {user.role}</p>
                    <div className="mt-10 p-10 border-4 border-dashed border-blue-200 rounded-xl text-center">
                        <p className="text-blue-400">Связь с базой Supabase установлена. Ты внутри!</p>
                        <button onClick={() => window.location.reload()} className="mt-4 text-red-500 underline text-sm">Выйти</button>
                    </div>
                </div>
            );
        }

        const root = ReactDOM.createRoot(document.getElementById('root'));
        root.render(<App />);
    </script>
</body>
</html>
