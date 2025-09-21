# Programação Científica - Algoritmos Numéricos

Este projeto implementa em Julia os problemas de programação científica relacionados a:
1. Diferenças finitas
2. Equação diferencial ordinária de primeira ordem

## Estrutura do Projeto

- `problema1.jl` - Implementação da função f(x) = e^(x*sen(ax))e^(-bx)
- `problema2.jl` - Resolução da Lei Fundamental da Dinâmica usando MDF

## Problemas Implementados

### PROBLEMA 1
**Função:** f(x) = e^(x*sen(ax))e^(-bx)

**Parâmetros sugeridos:**
- a = 3.0
- b = 2.0  
- c = 10.0
- d = 2.0

**Funcionalidades:**
- Cálculo da função para valores específicos
- Cálculo da derivada numérica usando diferenças finitas
- Plotagem do gráfico da função e sua derivada
- Intervalo: x ∈ [0, 2]

### PROBLEMA 2  
**Equação:** Lei Fundamental da Dinâmica - m(dv/dt) = mg - αv(t)

**Parâmetros:**
- m = 1.0 kg (massa)
- α = 1.0 N·s/m (coeficiente de arraste)
- g = 9.8 m/s² (aceleração da gravidade)
- v₀ = 0 m/s (velocidade inicial)
- Intervalo: t ∈ [0, 5] s

**Funcionalidades:**
- Resolução numérica usando Método das Diferenças Finitas (MDF/Euler)
- Comparação com solução analítica
- Cálculo da velocidade limite
- Análise de erro entre soluções numérica e analítica
- Plotagem dos resultados

## Como Executar

### Pré-requisitos
- Julia instalado (versão 1.6 ou superior)
- Pacote Plots.jl

### Execução
```bash
julia main.jl
```

Ou execute os problemas individualmente:
```bash
julia problema1.jl
julia problema2.jl
```

### Instalação de Dependências
O script principal verifica e instala automaticamente os pacotes necessários. Para instalação manual:

```julia
using Pkg
Pkg.add("Plots")
```

## Métodos Numéricos Utilizados

### Diferenças Finitas (Problema 1)
- Cálculo da derivada: f'(x) ≈ [f(x+h) - f(x)]/h
- h = 1e-8 (passo pequeno para precisão)

### Método de Euler (Problema 2)  
- Discretização: v_{j+1} = v_j + Δt * (g - (α/m) * v_j)
- Implementação do MDF para equação diferencial de primeira ordem
- Comparação com solução analítica: v(t) = (mg/α)(1 - e^(-αt/m))

## Análise dos Resultados

### Velocidade Limite
A velocidade limite teórica é calculada como:
```
v_limite = mg/α = (1.0 × 9.8)/1.0 = 9.8 m/s
```

### Precisão Numérica
O método MDF apresenta boa concordância com a solução analítica, com erros típicos na ordem de 10⁻⁶ m/s.

## Visualizações

Os gráficos gerados mostram:
1. **Problema 1**: Comportamento oscilatório decrescente da função exponencial
2. **Problema 2**: Crescimento assintótico da velocidade até o limite teórico

## Autor
Implementação em Julia baseada no material de Programação Científica - Algoritmos Numéricos

