-- Função para procurar o modelo do carro pelo nome no jogo
function procurarCarroPeloNome(nomeDoCarro)
    -- Vamos definir as pastas a serem verificadas
    local pastasParaProcurar = {
        game:GetService("ReplicatedStorage"),
        game:GetService("ServerStorage"),
        game:GetService("Workspace"),
    }

    -- Vamos procurar pelo nome do carro nessas pastas
    for _, pasta in ipairs(pastasParaProcurar) do
        print("Procurando pelo carro: " .. nomeDoCarro .. " em " .. pasta.Name)
        
        -- Verificar todos os objetos na pasta
        for _, item in ipairs(pasta:GetChildren()) do
            -- Verificar se o item é um modelo com o nome correspondente
            if item:IsA("Model") and item.Name == nomeDoCarro then
                print("Carro encontrado: " .. item.Name .. " em " .. pasta.Name)
                -- Você pode retornar o modelo ou realizar outras ações aqui
                return item
            end
        end
    end

    print("Carro não encontrado.")
    return nil
end

-- Defina o nome do carro que você quer procurar (por exemplo, "Mazda4")
local nomeDoCarro = "Mazda4"
procurarCarroPeloNome(nomeDoCarro)
