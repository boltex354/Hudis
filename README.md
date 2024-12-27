 Função para calcular a distância entre dois pontos
function calcularDistancia(p1, p2)
    return math.sqrt((p2.x - p1.x)^2 + (p2.y - p1.y)^2)
end

-- Função para encontrar o inimigo mais próximo
function encontrarInimigoMaisProximo(jogador, inimigos)
    local inimigoMaisProximo = nil
    local menorDistancia = math.huge

    for _, inimigo in ipairs(inimigos) do
        local distancia = calcularDistancia(jogador.posicao, inimigo.posicao)
        if distancia < menorDistancia then
            menorDistancia = distancia
            inimigoMaisProximo = inimigo
        end
    end

    return inimigoMaisProximo
end

-- Função para ativar o aimbot
function ativarAimbot(jogador, inimigos)
    local alvo = encontrarInimigoMaisProximo(jogador, inimigos)
    if alvo then
        -- Aqui você pode adicionar a lógica para "grudar" na cabeça do inimigo
        -- Por exemplo, ajustar a mira do jogador para a posição da cabeça do inimigo
        jogador.mira = {x = alvo.posicao.x, y = alvo.posicao.y + alturaCabeca} -- alturaCabeca é a altura da cabeça do inimigo
    end
end
