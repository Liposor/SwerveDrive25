# Swerve Drive no FRC

O **swerve drive** é um dos sistemas de locomoção mais avançados utilizados em robôs de FRC. Ele oferece alta manobrabilidade, permitindo que o robô se mova em qualquer direção independentemente da orientação do chassi.

## 1 - Funcionamento Mecânico

No swerve drive, cada roda é montada em um módulo independente que pode girar 360° (rotação) e também é acionado para mover o robô (tração). Cada módulo possui:

- **Motor de Tração:** Responsável por girar a roda para frente ou para trás.
- **Motor de Rotação (Steering):** Gira o módulo para alterar a direção da roda.
- **Encoder:** Mede o ângulo de rotação do módulo para controle preciso.

**Vantagens Mecânicas:**
- Movimentação omnidirecional (para frente, trás, lateral e diagonal).
- Capacidade de girar sobre o próprio eixo enquanto se move em qualquer direção.
- Grande agilidade em campo.

**Desvantagens:**
- Complexidade mecânica e de montagem.
- Necessidade de manutenção e calibração frequentes.

## 2 - Funcionamento Lógico

O controle lógico do swerve drive envolve cálculos para determinar a velocidade e o ângulo de cada módulo, baseando-se nos comandos de movimento desejados (translação e rotação).

### Passos Lógicos Básicos:

1. **Leitura dos Comandos:** Recebe comandos de joystick para translação (X, Y) e rotação (Z).
2. **Cálculo Vetorial:** Calcula o vetor de movimento desejado para cada módulo, combinando translação e rotação.
3. **Determinação de Ângulo e Velocidade:** Para cada módulo, calcula:
    - O ângulo que o módulo deve apontar.
    - A velocidade que a roda deve girar.
4. **Controle dos Motores:** Envia comandos para os motores de tração e rotação de cada módulo, usando feedback dos encoders para precisão.
5. **Normalização:** Garante que nenhuma roda ultrapasse a velocidade máxima permitida.

### Exemplo de Lógica Simplificada (Pseudocódigo):

```java
for (cada módulo do swerve) {
     // Calcula o vetor de movimento para o módulo
     double targetAngle = calcularAngulo(translacaoX, translacaoY, rotacao, posicaoModulo);
     double targetSpeed = calcularVelocidade(translacaoX, translacaoY, rotacao, posicaoModulo);

     // Ajusta o ângulo do módulo usando o motor de rotação
     modulo.setAngle(targetAngle);

     // Ajusta a velocidade da roda usando o motor de tração
     modulo.setSpeed(targetSpeed);
}
```

### Considerações de Software:

- **PID Controllers:** Usados para controlar precisamente o ângulo dos módulos.
- **Odometry:** Utilizada para rastrear a posição do robô no campo.
- **Field-Oriented Control:** Permite que o robô se mova em relação ao campo, não apenas ao chassi.

## 3 - Recursos Úteis

- [Documentação oficial do WPILib sobre Swerve](https://docs.wpilib.org/en/stable/docs/software/examples-tutorials/robot-classes/swerve-drive.html)
- [Vídeo explicativo sobre Swerve Drive (YouTube)](https://www.youtube.com/watch?v=8Fz1JzJkYJ4)

---

O swerve drive é uma solução poderosa para robôs de FRC que buscam máxima mobilidade e controle, mas exige atenção especial tanto na parte mecânica quanto na lógica de programação.
