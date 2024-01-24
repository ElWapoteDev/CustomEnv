## Documentación para la Clase advices en wax

La clase `advices` de wax permite enviar avisos a un cliente específico.

### Métodos:

#### `SendFakeAdvice(jugador: Player, titulo: string, contenido: string, mensajeDeKick: string) -> tuple success: boolean, error: string`

Envía un mensaje con la estética de un prompt de Roblox con la finalidad de jugarle una broma al usuario.

- `jugador`: La instancia del jugador al que se enviará el mensaje.
- `titulo`: El título que tendrá el aviso.
- `contenido`: El contenido del aviso.
- `mensajeDeKick`: En caso de que el jugador presione salir, esta será la razón del kick.

**Retorno:**
- `success`: Booleano indicando si el mensaje se envió correctamente.
- `error`: Mensaje de error en caso de que haya algún problema.

### Ejemplo de Código:

```lua
local advices = from('wax'):import('advices')
local victima = game.Players.JohnDoe

local success, error = advices.SendFakeAdvice(victima, 'Baneado', 'Has sido baneado permanentemente por incumplir las normas', 'Te trolie')

if success then
    print("Mensaje enviado con éxito")
else
    warn("Error al enviar el mensaje:", error)
end
```
