---
layout: post
published: true
title: Descriptción paquete CCSDS
---


[Ruby desde Java](https://www.ruby-lang.org/es/documentation/ruby-from-other-languages/to-ruby-from-java/)

## Ruby en 20 mins
[https://www.ruby-lang.org/es/documentation/quickstart/4/](https://www.ruby-lang.org/es/documentation/quickstart/4/)

```
irb(main):001:0> "Hola Mundo"
=> "Hola Mundo"
```


```
irb(main):015:0> def h(nombre)
irb(main):016:1> puts "Hola #{nombre}"
irb(main):017:1> end
=> nil
irb(main):018:0> h("Matz")
Hola Matz
=> nil

```

```
irb(main):024:0> class Anfitrion
irb(main):025:1>   def initialize(nombre = "Mundo")
irb(main):026:2>     @nombre = nombre
irb(main):027:2>   end
irb(main):028:1>   def decir_hola
irb(main):029:2>     puts "Hola #{@nombre}"
irb(main):030:2>   end
irb(main):031:1>   def decir_adios
irb(main):032:2>     puts "Adiós #{@nombre}, vuelve pronto."
irb(main):033:2>   end
irb(main):034:1> end
=> nil
```

```
irb(main):035:0> a = Anfitrion.new("Juan")
=> #<Anfitrion:0x16cac @nombre="Juan">
irb(main):036:0> a.decir_hola
Hola Juan
=> nil
irb(main):037:0> a.decir_adios
Adiós Juan, vuelve pronto.
=> nil
```

```
irb(main):038:0> a.@nombre
SyntaxError: compile error
(irb):52: syntax error
        from (irb):52
```
No se puede acceder a los atributos como en Java. Solo se puede acceder a través de métodos.

```
#!/usr/bin/env ruby

class MegaAnfitrion
  attr_accessor :nombres

  # Crear el objeto
  def initialize(nombres = "Mundo")
    @nombres = nombres
  end

  # Decirle hola a todos
  def decir_hola
    if @nombres.nil?
      puts "..."
    elsif @nombres.respond_to?("each")
      # @nombres es una lista de algún tipo,
      # ¡así que podemos iterar!
      @nombres.each do |nombre|
        puts "Hola #{nombre}"
      end
    else
      puts "Hola #{@nombres}"
    end
  end

  # Decirle adiós a todos
  def decir_adios
    if @nombres.nil?
      puts "..."
    elsif @nombres.respond_to?("join")
      # Juntar los elementos de la lista
      # usando la coma como separador
      puts "Adiós #{@nombres.join(", ")}. Vuelvan pronto."
    else
      puts "Adiós #{@nombres}. Vuelve pronto."
    end
  end

end


if __FILE__ == $0
  ma = MegaAnfitrion.new
  ma.decir_hola
  ma.decir_adios

  # Cambiar el nombre a "Diego"
  ma.nombres = "Diego"
  ma.decir_hola
  ma.decir_adios

  # Cambiar el nombre a un vector de nombres
  ma.nombres = ["Alberto", "Beatriz", "Carlos",
    "David", "Ernesto"]
  ma.decir_hola
  ma.decir_adios

  # Cambiarlo a nil
  ma.nombres = nil
  ma.decir_hola
  ma.decir_adios
end
```
Salida:
```
Hola Mundo
Adiós Mundo. Vuelve pronto.
Hola Diego
Adiós Diego. Vuelve pronto.
Hola Alberto
Hola Beatriz
Hola Carlos
Hola David
Hola Ernesto
Adiós Alberto, Beatriz, Carlos, David, Ernesto. Vuelvan pronto.
...
...
```
