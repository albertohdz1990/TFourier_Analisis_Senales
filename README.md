import numpy as np
import matplotlib.pyplot as plt

# Definición del tiempo
t = np.linspace(-1, 1, 1000)

# Señales básicas
pulso = np.where(np.abs(t) <= 0.2, 1, 0)
escalon = np.where(t >= 0, 1, 0)
senoidal = np.sin(2 * np.pi * 5 * t)

# FFT para el pulso
fft_pulso = np.fft.fft(pulso)
freq = np.fft.fftfreq(len(t), d=(t[1] - t[0]))

# Graficar pulso y su espectro
plt.figure(figsize=(12, 6))
plt.subplot(3,1,1)
plt.plot(t, pulso)
plt.title("Pulso Rectangular")

plt.subplot(3,1,2)
plt.plot(freq, np.abs(fft_pulso))
plt.title("Magnitud FFT del Pulso")

plt.subplot(3,1,3)
plt.plot(freq, np.angle(fft_pulso))
plt.title("Fase FFT del Pulso")

plt.tight_layout()
plt.show()

