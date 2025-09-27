# Programação Científica - Algoritmos Numéricos

Este projeto implementa em Julia os problemas de programação científica relacionados a:
1. Diferenças finitas
2. Equação diferencial ordinária de primeira ordem
3. Integração numérica usando regra de Simpson
4. Equação diferencial ordinária de segunda ordem

## Estrutura do Projeto

- `problema1.jl` - Implementação da função f(x) = e^(x*sen(ax))e^(-bx)
- `problema2.jl` - Resolução da Lei Fundamental da Dinâmica usando MDF
- `problema3.ipynb` - Integração numérica com regra de Simpson
- `problema4.ipynb` - Equação diferencial de segunda ordem (sistema de EDOs)

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

### PROBLEMA 3
**Integral:** ∫₀^(π/2) sin²(x) dx = π/4 ≈ 0.785398163397...

**Método:** Regra de Simpson
- Fórmula: ∫ₐᵇ f(x)dx = (s₀ + 4s₁ + 2s₂) · Δx/3
- s₀ = f(a) + f(b)
- s₁ = Σf(x_{2j+1}) (pontos ímpares)
- s₂ = Σf(x_{2j}) (pontos pares internos)

**Funcionalidades:**
- Implementação da regra de Simpson
- Verificação de precisão em função do número de pontos
- Comparação com valor exato conhecido
- Visualização da função e pontos de discretização
- Análise de convergência numérica

### PROBLEMA 4
**Equação:** EDO de 2ª ordem - m(d²x/dt²) = mg - αv(t)

**Sistema de EDOs de 1ª ordem:**
- u₁ = x (posição)
- u₂ = v = dx/dt (velocidade)
- du₁/dt = u₂
- du₂/dt = g - (α/m)u₂

**Parâmetros:**
- m = 1.0 kg (massa)
- α = 1.0 N·s/m (coeficiente de arraste)
- g = 9.8 m/s² (aceleração da gravidade)
- Condições iniciais: x₀ = 0 m, v₀ = 0 m/s
- Intervalo: t ∈ [0, 5] s

**Funcionalidades:**
- Resolução numérica usando método de Euler para sistemas
- Comparação com solução analítica para posição e velocidade
- Visualização da trajetória no espaço de fases
- Análise de convergência para velocidade limite
- Plotagem de posição vs tempo e velocidade vs tempo

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

### Regra de Simpson (Problema 3)
- Integração numérica: ∫ₐᵇ f(x)dx = (s₀ + 4s₁ + 2s₂) · Δx/3
- Aproximação polinomial de grau 2 em cada subintervalo
- Convergência de ordem O(h⁴) para funções suaves

### Sistema de EDOs - Método de Euler (Problema 4)
- Transformação de EDO de 2ª ordem em sistema de 1ª ordem
- Discretização: u_{j+1} = u_j + Δt * f(t_j, u_j)
- Solução analítica: x(t) = (mg/α)[t + (m/α)(e^(-αt/m) - 1)] + x₀

## Análise dos Resultados

### Velocidade Limite (Problemas 2 e 4)
A velocidade limite teórica é calculada como:
```
v_limite = mg/α = (1.0 × 9.8)/1.0 = 9.8 m/s
```

### Precisão Numérica
- **Problema 2**: O método MDF apresenta boa concordância com a solução analítica, com erros típicos na ordem de 10⁻⁶ m/s
- **Problema 3**: A regra de Simpson converge rapidamente para o valor exato π/4 ≈ 0.785398
- **Problema 4**: O sistema de EDOs mantém consistência física, convergindo para velocidade limite

### Integração de Simpson (Problema 3)
O valor exato da integral ∫₀^(π/2) sin²(x) dx = π/4 é usado como referência para verificar a precisão do método numérico.

## Visualizações

Os gráficos gerados mostram:
1. **Problema 1**: Comportamento oscilatório decrescente da função exponencial
2. **Problema 2**: Crescimento assintótico da velocidade até o limite teórico
3. **Problema 3**: Visualização da função sin²(x) e pontos de discretização
4. **Problema 4**: Trajetórias de posição e velocidade, incluindo espaço de fases

## Autor
Implementação em Julia baseada no material de Projetos Computacionais no Ensino de Física - FISC61

