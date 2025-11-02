const Leaderboard = {
    async load() {
        try {
            const res = await fetch('assets/leaderboard.json');
            return await res.json();
        } catch {
            return JSON.parse(localStorage.getItem('crystalLeaderboard') || '[]');
        }
    },
    async save(data) {
        localStorage.setItem('crystalLeaderboard', JSON.stringify(data));
        // В реальности — POST на сервер
    },
    async add(name, score) {
        const data = await this.load();
        data.push({ name, score, date: new Date().toLocaleDateString() });
        data.sort((a,b) => b.score - a.score);
        await this.save(data.slice(0, 10));
    },
    async show(container) {
        const data = await this.load();
        container.innerHTML = data.map((e, i) => `
            <div class="lb-item">
                <span>${i+1}. ${e.name}</span>
                <span>${e.score} очков</span>
            </div>
        `).join('') || '<p>Пока нет рекордов</p>';
    }
};
