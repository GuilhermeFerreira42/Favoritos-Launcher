/**
 * ===================================================================================
 * DOCUMENTAÇÃO DAS FUNÇÕES JAVASCRIPT
 * ===================================================================================
 * * Este documento descreve todas as funções utilizadas no sistema de gerenciamento
 * de favoritos.
 */

// --- Funções de Exportação ---

/**
 * Gera uma string HTML contendo todos os favoritos, no formato compatível com
 * o padrão NETSCAPE-Bookmark-file-1, usado para importação em navegadores.
 * A função interna buildHtmlForGroups navega recursivamente pela estrutura de 
 * grupos e subgrupos.
 * @returns {string} Uma string HTML completa pronta para ser exportada.
 */
function generateExportHTML() { /* ...código... */ }

/**
 * Inicia o download do arquivo de favoritos.
 * Ela chama generateExportHTML() para obter o conteúdo, cria um Blob,
 * gera uma URL temporária e simula um clique em um link para baixar o arquivo.
 */
function exportFavorites() { /* ...código... */ }


// --- Camada de Lógica e Persistência ---

/**
 * Carrega os dados dos favoritos do localStorage. Se não houver dados salvos,
 * utiliza a estrutura de dados 'defaultData' e a salva para o primeiro uso.
 * Os dados carregados são armazenados na variável global 'appData'.
 */
function loadData() { /* ...código... */ }

/**
 * Salva o estado atual da variável 'appData' no localStorage,
 * convertendo o objeto para uma string JSON.
 */
function saveData() { /* ...código... */ }


// --- Funções de Papel de Parede ---

/**
 * Aplica a imagem de fundo salva em 'appData.background' ao corpo do documento.
 * Se nenhuma imagem estiver salva, aplica o gradiente CSS padrão.
 */
function applyWallpaper() { /* ...código... */ }

/**
 * Manipula o evento de seleção de um arquivo de imagem.
 * Lê o arquivo selecionado como um DataURL (Base64) e o salva em 'appData.background'.
 * @param {Event} event - O evento 'change' do input de arquivo.
 */
function handleWallpaperSelect(event) { /* ...código... */ }

/**
 * Aciona programaticamente o clique no input de arquivo de papel de parede,
 * que está oculto, para abrir a janela de seleção de arquivo do sistema operacional.
 */
function openWallpaperSelector() { /* ...código... */ }

/**
 * Restaura o papel de parede para o padrão, definindo 'appData.background' como null
 * e reaplicando o estilo (que voltará a ser o gradiente).
 */
function restoreDefaultWallpaper() { /* ...código... */ }


// --- Funções de Importação ---

/**
 * Função principal que inicia o parsing de um arquivo de favoritos do Chrome.
 * @param {string} htmlString - O conteúdo do arquivo HTML como uma string.
 * @returns {Array} Uma árvore de objetos representando a estrutura do arquivo.
 */
function parseBookmarks(htmlString) { /* ...código... */ }

/**
 * Constrói recursivamente uma árvore de objetos a partir dos elementos DOM
 * de um arquivo de favoritos. Distingue entre pastas (<H3>) e favoritos (<A>).
 * @param {HTMLElement} dlElement - O elemento <DL> a ser percorrido.
 * @returns {Array} Um array de objetos, onde cada objeto pode ser do tipo 'folder' ou 'bookmark'.
 */
function buildTree(dlElement) { /* ...código... */ }

/**
 * Converte a árvore de objetos genérica (gerada por buildTree) para o formato
 * de dados específico da aplicação (appData).
 * @param {Array} tree - A árvore de objetos a ser convertida.
 * @returns {Array} Um array de grupos no formato esperado por 'appData.groups'.
 */
function convertTreeToAppGroups(tree) { /* ...código... */ }

/**
 * Função auxiliar e recursiva que converte um objeto 'folder' da árvore genérica
 * em um objeto 'group' da aplicação, incluindo seus favoritos e subgrupos.
 * @param {object} folder - O objeto da pasta a ser convertido.
 * @param {string} id - O ID único a ser atribuído ao novo grupo.
 * @returns {object} Um objeto de grupo completo no formato da aplicação.
 */
function convertFolderToGroup(folder, id) { /* ...código... */ }

/**
 * Manipula o evento de seleção de um arquivo de favoritos para importação.
 * Lê o conteúdo do arquivo e orquestra o processo de parsing e conversão.
 * @param {Event} event - O evento 'change' do input de arquivo.
 */
function handleImportSelect(event) { /* ...código... */ }

/**
 * Aciona programaticamente o clique no input de arquivo de importação.
 */
function openImportSelector() { /* ...código... */ }


// --- Camada de Apresentação (Renderização) ---

/**
 * Função principal de renderização. Limpa o contêiner de grupos e inicia
 * o processo de renderização hierárquica a partir do nível raiz de 'appData.groups'.
 */
function render() { /* ...código... */ }

/**
 * Renderiza recursivamente os grupos e seus subgrupos na interface.
 * Cria os elementos HTML para cada grupo, seus favoritos e chama a si mesma
 * para renderizar os subgrupos, aplicando estilos diferentes se for um subgrupo.
 * @param {Array} groups - O array de grupos (ou subgrupos) a ser renderizado.
 * @param {HTMLElement} container - O elemento DOM onde os grupos serão inseridos.
 * @param {boolean} [isSubgroup=false] - Flag para indicar se a renderização é de um subgrupo.
 */
function renderHierarquia(groups, container, isSubgroup = false) { /* ...código... */ }


// --- Funções de Lógica Principal (dentro de DOMContentLoaded) ---

/**
 * Função auxiliar crucial que busca um grupo (ou subgrupo) em qualquer nível
 * da estrutura de dados 'appData'.
 * @param {string} groupId - O ID do grupo a ser encontrado.
 * @param {Array} groupsArray - O array de grupos onde a busca deve começar.
 * @returns {object|null} Um objeto contendo o grupo encontrado (`group`),
 * o array ao qual ele pertence (`parentArray`) e seu índice (`index`), ou null se não for encontrado.
 */
function findGroupData(groupId, groupsArray) { /* ...código... */ }

/**
 * Manipula o movimento do ponteiro (mouse/toque) durante o arraste de um grupo.
 * É responsável por criar o placeholder, aplicar estilos de "arrastando" e
 * mover o elemento pela tela. Também detecta se o cursor está sobre outro grupo
 * para indicar um possível aninhamento.
 * @param {PointerEvent} e - O evento de ponteiro.
 */
function onGroupPointerMove(e) { /* ...código... */ }

/**
 * Finaliza a operação de arrastar e soltar de um grupo.
 * Verifica se o grupo foi solto sobre outro (aninhamento) ou em um espaço vazio (reordenação).
 * Atualiza a estrutura de dados 'appData', salva e renderiza novamente a interface.
 * Realiza a limpeza de variáveis e classes de estado.
 * @param {PointerEvent} e - O evento de ponteiro.
 */
function onGroupPointerUp(e) { /* ...código... */ }


/**
 * Abre e configura o modal para adicionar ou editar um favorito.
 * @param {boolean} isEdit - Define se o modal está em modo de edição.
 * @param {object|null} [favorite=null] - O objeto do favorito a ser editado. Se for null, o modal abre em modo de criação.
 */
function openModal(isEdit, favorite = null) { /* ...código... */ }

/**
 * Fecha o modal de adicionar/editar favorito e reseta seu formulário e variáveis de estado.
 */
function closeModal() { /* ...código... */ }