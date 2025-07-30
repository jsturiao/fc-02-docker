# Full Cycle Rocks - Desafio Go

Este projeto é uma solução para o desafio de criar uma aplicação Go que imprime "Full Cycle Rocks!!" em uma imagem Docker de menos de 2MB.

## Como executar

### Localmente
```bash
go run main.go
```

### Docker

#### Construir a imagem
```bash
docker build -t jsturiao/fullcycle .
```

#### Executar a imagem
```bash
docker run jsturiao/fullcycle
```

#### Verificar o tamanho da imagem
```bash
docker images jsturiao/fullcycle
```

## Estratégia para menos de 2MB

1. **Multi-stage build**: Usa uma imagem com Go para compilar e depois copia apenas o binário para uma imagem `scratch`
2. **Compilação otimizada**: Usa flags `-ldflags "-s -w"` para remover símbolos de debug
3. **CGO desabilitado**: `CGO_ENABLED=0` evita dependências C
4. **Imagem scratch**: A menor imagem possível, contendo apenas o que é necessário

## Resultado esperado

```
Full Cycle Rocks!!
```

## Docker Hub

A imagem está disponível em: `jsturiao/fullcycle`

Para executar diretamente do Docker Hub:
```bash
docker run jsturiao/fullcycle
```
