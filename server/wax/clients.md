## Clase 'clients' - Documentación

Esta clase proporciona métodos relacionados con la manipulación de clientes.

### Métodos:

#### `ExecuteClientAsync(Player: Instance, code: string, chunk_name: string, env: {[string]: any}) -> Tuple<boolean, string>`

- **Player:** La instancia del jugador al que se ejecutará el código.
- **code:** El código Lua que se enviará al cliente.
- **chunk_name:** El nombre del código que se mostrará en el output del ejecutor.
- **env:** El entorno personalizado. Puedes enviar funciones en el entorno; estas se procesarán automáticamente y podrán usarse en el cliente. Ten en cuenta que el entorno personalizado se sumará al entorno que ya tiene el cliente.

**Retorna:** Un tuple con dos valores, `succ` (éxito, booleano) y `error` (mensaje de error, string).

### Ejemplo de Código:

```lua
local clients = from("wax"):import("clients")
local victima = OwnerPlayer

function contarServerStorage()
    return #game.ServerStorage:GetChildren()
end

local Codigo = [[
    local Nombre = nombreVictima
    print(Nombre)
    local NumeroInstanciasServerStorage = contarServerStorage()
    print('En Server Storage hay ' .. tostring(NumeroInstanciasServerStorage) .. ' instancias')
]]

local succ, err = clients.ExecuteClientAsync(victima, Codigo, 'Test.luau', {nombreVictima = victima.Name, contarServerStorage = contarServerStorage})

if succ then
    print("Código ejecutado con éxito en el cliente de " .. victima.Name)
else
    warn("Error al ejecutar el código en el cliente:", err)
end
```
