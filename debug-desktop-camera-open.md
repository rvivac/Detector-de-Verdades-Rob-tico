[OPEN] Desktop camera open

# Sessao
- session_id: `desktop-camera-open`
- data: 2026-06-17
- sintoma: a camera nao ativa no computador durante o teste local
- objetivo: descobrir com evidencia se a falha esta na permissao, na selecao do dispositivo, no carregamento do detector facial ou no fluxo de inicializacao

# Hipoteses
1. A chamada `getUserMedia()` falha no computador porque a preferencia por camera traseira nao encontra dispositivo compativel.
2. O carregamento do detector facial falha antes da webcam abrir e interrompe o fluxo de inicializacao.
3. A permissao de camera no navegador esta negada, bloqueada ou sendo recusada pelo ambiente local.
4. A webcam abre, mas o `play()` do elemento `video` falha e o app trata isso como indisponibilidade total.
5. Outro aplicativo ou driver esta ocupando a webcam e provoca erro de leitura no navegador.

# Plano
1. Instrumentar apenas o fluxo de inicializacao da camera.
2. Reproduzir localmente e coletar logs.
3. Confirmar ou rejeitar as hipoteses com base nos logs.
4. Aplicar a menor correcao possivel.
5. Verificar novamente com logs pos-correcao.
