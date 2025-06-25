#Ojetivo do Código

O código implementa o controle de um goleiro automático usando ESP32, sensores ultrassônicos e um servo motor. Ele mede a distância em 6 quadrantes com sensores, e quando detecta uma bola próxima (até 13 cm), move o servo motor para a posição correspondente para defender. A dificuldade pode ser ajustada via Bluetooth, alterando o tempo de reação (Fácil, Médio ou Difícil). O servo retorna à posição inicial após cada defesa.
