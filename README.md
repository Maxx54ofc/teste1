-- Função para procurar o modelo do carro pelo nome em todo o jogo
function procurarCarroEmTodoJogo(nomeDoCarro)
    -- Função recursiva para percorrer todas as pastas do jogo
    local function procurarEmPastas(pasta)
        -- Verificar todos os objetos na pasta
        for _, item in ipairs(pasta:GetChildren()) do
            -- Se o item for um modelo e o nome for o que procuramos, retornamos
            if item:IsA("Model") and item.Name == nomeDoCarro then
                print("Carro encontrado: " .. item.Name .. " em " .. pasta.Name)
                return item
            end
            
            -- Se o item for uma pasta, chamamos a função recursivamente
            if item:IsA("Folder") or item:IsA("Model") then
                local encontrado = procurarEmPastas(item)
                if encontrado then
                    return encontrado
                end
            end
        end
        return nil
    end

    -- Começar a busca em todas as partes do jogo
    local resultado = procurarEmPastas(game)
    
    if resultado then
        return resultado
    else
        print("Carro não encontrado em nenhum lugar.")
        return nil
    end
end

-- Defina o nome do carro que você quer procurar (por exemplo, "Maxma Fuji")
local nomeDoCarro = "Maxma Fuji"
procurarCarroEmTodoJogo(nomeDoCarro)
