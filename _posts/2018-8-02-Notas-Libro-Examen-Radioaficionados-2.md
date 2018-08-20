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

Es un generador de corriente se expresaría tal que así:

$$

V(t) = V_0 \cos{(\omega t + \phi_v)} = V_0 \cdot \text{Re}[e^{j (\omega t + \phi)}] = \text{Re}[V_0 e^{j\omega t} e^{j \phi)}]

\\

\text{Fasor:} \ V = V_0 e^{j \phi}

\\

V(t) = \text{Re}[V e^{j \omega t}]

\\

$$

Por tantos los fasores de V-I:

$$

V = V_0 e^{j \phi_V}


\qquad

I = I_0 e^{j \phi_I}

$$

## Impedancia

La **impedancia (Z)** es un término general que se puede aplicar a cualquier elemento (resistencia, bobina, condensador) o conjunto de elementos que opone una resistencia al paso de la **corriente alterna** por un circuito.

La impedancia **(Z)** se compone de la suma de la resistencia **(R)** y si **reactancia (X)**, esto es:

$$

Z = \frac{V}{I} \qquad Z = R + jX

$$

De igual forma, la **admitancia (Y)** es la inversa de la impedancia:

$$

Y = \frac{I}{V} = \frac{1}{Z} \qquad Y = G + jB

$$

La **admitancia** se compone de la **conductancia (G)** y de la **susceptancia (B)**.

### Resistencia

$$

V(t) = R i(t)

\\

V(t) = \text{Re} [V e^{jwt}] = R \ \text{Re} [I e^{j \omega t}] \Rightarrow \text{Re} [V e^{jwt}] - R \ \text{Re} [I e^{j \omega t}] = 0

\\

\text{Re} [(V - RI) e^{jwt}] = 0 \ , \forall t \Leftrightarrow (V - RI) = 0 \Rightarrow V = RI



$$

$$

Z_R = \frac{V}{I} = R

$$

Una resistencia **no desfasa la corriente respecto de la fase de la tensión**

$$

V_R = R \cdot I_R \quad \text{y} \quad \phi_V = \phi_i

$$

### Bobina

$$

V(t) = L \frac{d i}{dt}

\\

V(t) = \text{Re} [V e^{jwt}] = L \frac{d}{dt} \ \text{Re} [I e^{j \omega t}] = \text{Re} [L I j \omega e^{j \omega t}]

\\

\text{Re} [(V - j \omega L I) e^{jwt}] = 0 \ , \forall t \Leftrightarrow (V - j \omega L I) = 0 \Rightarrow V = j \omega L I

$$

$$

Z_L = \frac{V}{I} = j \omega L

$$

La **bobina desfasa la corriente \\(- \pi /2 \\) respecto de la fase de la tensión**:

$$

V(t) = L \frac{d i}{dt} = \omega L I_L \cos(\omega t + \phi_i) = \omega L I_L \sin(\omega t + \phi_i + 90º) = V_L \sin(\omega t + \phi_V)

\\

V_L = j \omega L I_L \quad \text{y} \quad \phi_V = \phi_i + 90º

$$

### Condensador

$$


i(t) = C \frac{d V}{dt}

\\

i(t) = \text{Re} [I e^{jwt}] = C \frac{d}{dt} \ \text{Re} [V e^{j \omega t}] = \text{Re} [C V j \omega e^{j \omega t}]

\\

\text{Re} [(I - j \omega C V) e^{jwt}] = 0 \ , \forall t \Leftrightarrow (I - j \omega C V) = 0 \Rightarrow I = j \omega C V \Rightarrow V = \frac{I}{j \omega C}
$$

$$

Z_C = \frac{V}{I} = \frac{1}{j \omega C} = - \frac{j}{\omega C}

$$

El **condensador desfasa la corriente \\(\pi /2 \\) respecto de la fase de la tensión**:

$$

i(t) = C \frac{d V}{dt} = \omega C V_C \cos(\omega t + \phi_V) = \omega C V_C \sin(\omega t + \phi_V + 90º) = I_C \sin(\omega t + \phi_I)

\\

V_C = \frac{I_C}{j \omega C} \quad \text{y} \quad \phi_V = \phi_i - 90º

$$

### Tabla de impedancias

| Componente | Z | Y | Relación funcional | Relación funcional en expresión fasorial | Relación entre fases |
|---|---|---|
| R | \\(R\\) | \\(\frac{1}{R}\\) | \\(V(t) = R i(t)\\) | \\(V = RI, I = V/R\\) | \\(\phi_v = \phi_i\\) |
| L | \\(j \omega L\\) | \\(\frac{1}{j \omega L}\\) | \\(V(t) = L \frac{di(t)}{dt}\\) | \\(V = j \omega L I, I = V / j \omega L\\) | \\(\phi_V = \phi_I + 90º\\)
| C | \\(\frac{1}{j \omega C}\\) | \\(j \omega C\\) | \\(i(t) = C \frac{dv(t)}{dt}\\) | \\(V = I/ j \omega C , I = j \omega C V\\) | \\(\phi_V = \phi_i - 90º\\)
