### Olá! meu nome é Vitor Ferreira 👋

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Galaxy Visualization</title>
    <style>
        body { 
            margin: 0; 
            overflow: hidden; 
            background: #000;
        }
        canvas { 
            display: block; 
            background: radial-gradient(ellipse at center, #0a0e27 0%, #000 100%);
        }
    </style>
</head>
<body>
    <canvas id="galaxyCanvas"></canvas>
    <script>
        const canvas = document.getElementById('galaxyCanvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        
        const particles = [];
        const particleCount = 2000;
        
        class Particle {
            constructor() {
                this.reset();
            }
            reset() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.vx = (Math.random() - 0.5) * 2;
                this.vy = (Math.random() - 0.5) * 2;
                this.life = Math.random() * 200 + 100;
                this.maxLife = this.life;
                this.size = Math.random() * 2 + 0.5;
            }
            update() {
                this.x += this.vx;
                this.y += this.vy;
                this.life--;
                if(this.life <= 0) this.reset();
            }
            draw() {
                ctx.fillStyle = `rgba(255, 255, 255, ${this.life / this.maxLife})`;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }
        
        for(let i = 0; i < particleCount; i++) {
            particles.push(new Particle());
        }
        
        function animate() {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.1)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => {
                p.update();
                p.draw();
            });
            requestAnimationFrame(animate);
        }
        animate();
        
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
    </script>
</body>
</html>
```

---

Apaixonado por tecnologia, buscando sempre melhorar o meu conhecimento e me aperfeiçoar cada vez mais, com as novas tecnologias.