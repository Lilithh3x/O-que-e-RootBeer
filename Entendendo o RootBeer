**O que é RootBeer? Para que serve?**

RootBeer é uma biblioteca de código aberto criada por [Scott Alexander (scottyab)](https://github.com/scottyab) e [Matthew Rollings (stealthcopter)](https://github.com/stealthcopter) em 2015. Seu objetivo é facilitar a implementação de detecção de dispositivos Android "rootados" para os desenvolvedores. Isso é uma preocupação significativa em termos de segurança e integridade para certos aplicativos.

**Mas o que é root?**

Se você não está familiarizado com o termo **Root** em dispositivos Android, aqui vai uma breve explicação: "Root" significa obter acesso total ao sistema. Em termos simples, é como ter privilégios de administrador no sistema operacional do dispositivo.

**Por que fazer root?**

"Rootar" oferece várias vantagens para os usuários, incluindo a capacidade de realizar alterações que não seriam possíveis de outra forma, como remover aplicativos pré-instalados ou modificar o kernel do dispositivo. No entanto, rootar também apresenta riscos: pode resultar na perda da garantia, danificar o dispositivo ou torná-lo mais vulnerável a malwares.

**Nota**: Fazer root é recomendado principalmente para aqueles que estão estudando ou testando a segurança de um aplicativo. Não é aconselhável para quem utiliza o celular no dia a dia.

Beleza, já que a gente já sabe o que é root e por que fazer, bora entender como o RootBeer funciona.

**Como funciona o RootBeer?**

O RootBeer executa uma série de testes para identificar sinais de root em um dispositivo. As verificações incluem:

**Verificações baseadas em Java**

**checkRootManagementApps** A verificação inicia-se pela leitura da lista de nomes de pacotes (APKs) que são conhecidos por gerenciar os acessos root no dispositivo, como o SuperSU e o Magisk Manager.

Depois de obter essa lista, o RootBeer faz uma varredura de todos os APKs instalados no dispositivo e obtém o nome de cada um. Então, ele verifica a presença dos APKs de gerenciamento de root, comparando-os com a lista de APKs conhecidos.

Com essa verificação concluída, o resultado do `checkRootManagementApps` mostrará se algum aplicativo da lista de gerenciamento de root foi identificado no dispositivo. Se nenhum desses aplicativos for encontrado, o RootBeer indicará que o dispositivo não está "rootado".

Principais aplicativos da lista de gerenciamento de root:

- [Magisk](https://magiskmanager.com/)
- [EdXposed](https://themagisk.com/edxposed/)
- [BusyBox](https://busybox.net/)
- [Titanium Backup](https://www.titaniumtrack.com/titanium-backup.html)**O que é RootBeer? Para que serve?**

RootBeer é uma biblioteca de código aberto criada por [Scott Alexander (scottyab)](https://github.com/scottyab) e [Matthew Rollings (stealthcopter)](https://github.com/stealthcopter) em 2015. Seu objetivo é facilitar a implementação de detecção de dispositivos Android "rootados" para os desenvolvedores. Isso é uma preocupação significativa em termos de segurança e integridade para certos aplicativos.

**Mas o que é root?**

Se você não está familiarizado com o termo **Root** em dispositivos Android, aqui vai uma breve explicação: "Root" significa obter acesso total ao sistema. Em termos simples, é como ter privilégios de administrador no sistema operacional do dispositivo.

**Por que fazer root?**

"Rootar" oferece várias vantagens para os usuários, incluindo a capacidade de realizar alterações que não seriam possíveis de outra forma, como remover aplicativos pré-instalados ou modificar o kernel do dispositivo. No entanto, rootar também apresenta riscos: pode resultar na perda da garantia, danificar o dispositivo ou torná-lo mais vulnerável a malwares.

**Nota**: Fazer root é recomendado principalmente para aqueles que estão estudando ou testando a segurança de um aplicativo. Não é aconselhável para quem utiliza o celular no dia a dia.

Beleza, já que a gente já sabe o que é root e por que fazer, bora entender como o RootBeer funciona.

**Como funciona o RootBeer?**

O RootBeer executa uma série de testes para identificar sinais de root em um dispositivo. As verificações incluem:

**Verificações baseadas em Java**

**checkRootManagementApps** A verificação inicia-se pela leitura da lista de nomes de pacotes (APKs) que são conhecidos por gerenciar os acessos root no dispositivo, como o SuperSU e o Magisk Manager.

Depois de obter essa lista, o RootBeer faz uma varredura de todos os APKs instalados no dispositivo e obtém o nome de cada um. Então, ele verifica a presença dos APKs de gerenciamento de root, comparando-os com a lista de APKs conhecidos.

Com essa verificação concluída, o resultado do `checkRootManagementApps` mostrará se algum aplicativo da lista de gerenciamento de root foi identificado no dispositivo. Se nenhum desses aplicativos for encontrado, o RootBeer indicará que o dispositivo não está "rootado".

Principais aplicativos da lista de gerenciamento de root:

- [Magisk](https://magiskmanager.com/)
- [EdXposed](https://themagisk.com/edxposed/)
- [BusyBox](https://busybox.net/)
- [Titanium Backup](https://www.titaniumtrack.com/titanium-backup.html)
- [Lucky Patcher](https://www.luckypatchers.com/)

Esse método de verificação é semelhante aos checks seguintes:

- `checkPotentiallyDangerousApps`: Procura por aplicativos relacionados a atividades mal-intencionadas, como ferramentas de hacking e aplicativos que exploram vulnerabilidades.
- `checkRootCloakingApps`: Identifica se há algum app destinado a ocultar o status de root do dispositivo.
- `checkForDangerousProps`: Analisa os valores de várias propriedades do sistema que só podem ser modificados se o dispositivo estiver rootado.
- `checkForBusyBoxBinary`: Procura pela existência do binário BusyBox no Android.
- `checkForSuBinary(Native checks)/checkSuExists`: Verifica a presença do binário "su" no dispositivo.
 
_NOTA: Por padrão, a verificação do binário BusyBox no RootBeer está desativada. Se for necessário, essa verificação pode ser habilitada isoladamente ou em conjunto com outras verificações de root disponíveis na biblioteca._

**checkForRWSystem/checkForRWPaths** As verificações `checkForRWSystem` e `checkForRWPaths` são similares e analisam o sistema de arquivos para ver se a partição "/system" tem permissão somente de leitura (read-only) ou permissões de leitura e escrita (read-write).

Essas verificações determinam o tipo de permissão da partição "/system" para identificar se é read-only ou read-write.

**checkTestKeys**
A verificação de assinatura `checkTestKeys` tem como objetivo detectar se um aplicativo Android foi assinado usando chaves de teste em vez de chaves de produção.

O funcionamento dessa verificação é simples e consiste em duas etapas:

1. **Aquisição da assinatura do certificado**: A verificação acessa a assinatura do certificado usado no app Android.

2. **Comparação com chaves de teste conhecidas**: Posteriormente, essa assinatura é comparada com uma lista de assinaturas de chaves de teste reconhecidas.

_NOTA: Os nomes de pacotes e caminhos(ex: /system) que o RootBeer utiliza nas verificações estão contidos em um único arquivo e podem ser modificados._

Embora o RootBeer se dedique principalmente à detecção de root, a segurança de aplicativos vai além dessa questão. Proteger aplicativos de root é essencial para prevenir fraudes e manipulações de dados; contudo, existem outras ameaças que não envolvem o root.

Espero que este breve resumo sobre o RootBeer tenha sido esclarecedor. Caso tenha se interessado pelo tema, recomendo visitar o [GitHub do RootBeer](https://github.com/scottyab/rootbeer) para obter mais informações.
- [Lucky Patcher](https://www.luckypatchers.com/)

Esse método de verificação é semelhante aos checks seguintes:

- `checkPotentiallyDangerousApps`: Procura por aplicativos relacionados a atividades mal-intencionadas, como ferramentas de hacking e aplicativos que exploram vulnerabilidades.
- `checkRootCloakingApps`: Identifica se há algum app destinado a ocultar o status de root do dispositivo.
- `checkForDangerousProps`: Analisa os valores de várias propriedades do sistema que só podem ser modificados se o dispositivo estiver rootado.
- `checkForBusyBoxBinary`: Procura pela existência do binário BusyBox no Android.
- `checkForSuBinary(Native checks)/checkSuExists`: Verifica a presença do binário "su" no dispositivo.
 
_NOTA: Por padrão, a verificação do binário BusyBox no RootBeer está desativada. Se for necessário, essa verificação pode ser habilitada isoladamente ou em conjunto com outras verificações de root disponíveis na biblioteca._

**checkForRWSystem/checkForRWPaths** As verificações `checkForRWSystem` e `checkForRWPaths` são similares e analisam o sistema de arquivos para ver se a partição "/system" tem permissão somente de leitura (read-only) ou permissões de leitura e escrita (read-write).

Essas verificações determinam o tipo de permissão da partição "/system" para identificar se é read-only ou read-write.

**checkTestKeys**
A verificação de assinatura `checkTestKeys` tem como objetivo detectar se um aplicativo Android foi assinado usando chaves de teste em vez de chaves de produção.

O funcionamento dessa verificação é simples e consiste em duas etapas:

1. **Aquisição da assinatura do certificado**: A verificação acessa a assinatura do certificado usado no app Android.

2. **Comparação com chaves de teste conhecidas**: Posteriormente, essa assinatura é comparada com uma lista de assinaturas de chaves de teste reconhecidas.

_NOTA: Os nomes de pacotes e caminhos(ex: /system) que o RootBeer utiliza nas verificações estão contidos em um único arquivo e podem ser modificados._

Embora o RootBeer se dedique principalmente à detecção de root, a segurança de aplicativos vai além dessa questão. Proteger aplicativos de root é essencial para prevenir fraudes e manipulações de dados; contudo, existem outras ameaças que não envolvem o root.

Espero que este breve resumo sobre o RootBeer tenha sido esclarecedor. Caso tenha se interessado pelo tema, recomendo visitar o [GitHub do RootBeer](https://github.com/scottyab/rootbeer) para obter mais informações.
