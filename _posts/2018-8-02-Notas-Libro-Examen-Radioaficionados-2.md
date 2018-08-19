---
layout: post
title: Libro De Examen de Radioaficionados - Capitulo 2
published: true
---

# Circuitos en corriente alterna. Filtros. Transformadores. Formas de onda no sinusoidales

### Sinusoides y fasores

Para simplificar las operaciones con sinusoides se utilizan los **fasores**. Un **fasor** es un número complejo que representa una sinusoide \\(x(t) = A \ \cos{(\omega t + \Phi)}\\).

#### Números complejo

//TODO foto de un número complejo

Se define cada número complejo z como un par ordenado de números reales: z = (a, b). A su vez el primer elemento a se define como parte real de z, se denota \\( a={\text{Re}}(z)\\) \\( a={\text{Re}}(z)\\); el segundo elemento b se define como parte imaginaria de z, se denota \\( b={\text{Im}}(z)\\) \\( b={\text{Im}}(z) \\)

$$

z = x + jy

\\

x = \text{Re} [z]   \qquad y = \text{Im} [z]

$$

Los número complejos se pueden expresar en su forma trigonométrica, pues (a, b) definen unas coordenadas en el plano complejo. Si r y \\(\theta\\) son las coordenadas polares del punto (x, y) (que corresponde a un número complejo no nulo z = x + jy ), es decir \\(x = r \ \cos{\theta}\\), \\(y = r \ \sin{\theta}\\) , el número \\(z \neq 0\\) puede escribirse:

$$

z = r(\cos{\theta} + j \sin{\theta})

$$

Si \\(z = 0 \ , \ \theta\\) es indefinido.

El número positivo \\(r = \lvert z \lvert = + \sqrt{x^2 + y^2}\\) es la longitud del vector correspondiente a z.

El número \\(\theta\\) (que puede calcularse mediante la ecuación \\(\tan{\theta} = \frac{y}{v}\\) ) se llama *argumento* de z y escribimos \\(\theta = arg \ z\\). Por tanto *arg z* denota un ángulo, en radianes, que forma el vector que representa z con el eje real positivo.

##### Fórmula de Euler

$$

e^{j\theta} = \cos{\theta} + j\sin{\theta}

$$

Con lo que un número *z* en su forma exponencial:

$$

z = r(\cos{\theta} + j \sin{\theta}) = r e^{j \theta}

$$

#### Fasores

Si tenemos una onda sinusoidal, el fasor que la representa será:

$$

x(t) = A_m \sin{(\omega t + \phi)}

$$

$$

x(t) = \text{Im} [A_m(\cos{(\omega t + \phi)} + j \sin{(\omega t + \phi)})]

\\

= \text{Im} [A_m e^{j(\omega t + \phi)}] = \text{Im} [A_m e^{j \phi} e^{j \omega t}]

$$

Por tanto el fasor que representa esta sinusoide es de la forma siguiente:

$$

X = A_m e^{j \phi}

$$

Por tanto *x(t)* será de la forma:

$$

x(t) = \text{Im} [X e^{j \omega t}]

$$

Por tanto un faso solo tiene información de su fase y de su amplitud. No tiene en cuenta la frecuencia con la que oscila la onda.

Para recuperar la onda que representa un fasor:

$$

x(t) = \text{Im} [X e^{j \omega t}] = \text{Im} [A_m e^{j \phi} e^{j \omega t}] = A_m \sin{(\omega t + \phi)}

$$

Es trivial decir:

$$

x(t) = \text{Re} [A e^{j \omega t}] = A_m \cos{(\omega t + \phi)}

\\

y(t) = \text{Im} [A e^{j \omega t}] = A_m \sin{(\omega t + \phi)}

$$
