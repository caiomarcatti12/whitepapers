# Descomplicando a cadeia de suprimentos de software "Supply Chain"

No Artigo [fix-version.md](../../container/fix-version/fix-version.md), levantei um ponto um tanto interessante, de certa forma ao consumir um repositório externo estou permitindo que terceiros contribuam com meu software, não só isso, mas permitindo que mesmo indiretamente eles manipulem meu software.

### Manipulando meu software

Quando digo "manipular o software", precisamos entender que não é só sobre código. Um software possui diversas camadas. Sim, o código final que produzimos é apenas a cereja do bolo 🎂.

### Camadas do Software

**Hardware:** Inclui CPU, memória, disco, placa de rede e periféricos que suportam o funcionamento do software.

**Firmware:** BIOS/UEFI inicializa e testa o hardware do computador durante o boot.

**Sistema Operacional:** O kernel, drivers, serviços de sistema e interface de usuário gerenciam e controlam o hardware e os recursos.

**Camada de Rede:** Protocolos de comunicação, firewalls e load balancers garantem a transmissão de dados e a proteção contra acessos não autorizados.

**Infraestrutura de Nuvem/Virtualização:** Máquinas virtuais, containers e serviços de nuvem oferecem recursos sob demanda e isolamento de ambientes de execução.

**Entre outros:** Serviços de Backend, Frontend, Código Fonte, Deploy…

Citei alguns componentes que presenciamos todo santo dia para que o software funcione corretamente ou aos trancos e barrancos, né!? #RealidadeCruel

### Importância dos Componentes

Tirando a parte software (backend/frontend), muitos nem dão bola para esses componentes, afinal, eles não são vistos. Se você escovar um bit em algum desses componentes, com certeza alguém vai te falar que é perda de tempo, a não ser que você esteja em uma empresa diferenciada com pessoas diferenciadas.

Mas no quesito segurança, não podemos dispensar nenhum componente ou camada, aliás, nem depositar nossa confiança neles.

**Camadas? Vamos à analogia.**

Pensa comigo, se olharmos para um carro ele de fato já é seguro, não é? De certa forma, se ocorrer uma pequena colisão, o impacto seria reduzido e/ou absorvido pela lataria.

Então, por que precisamos de um cinto de segurança? Porque, no caso da colisão, ele adiciona uma camada extra de proteção, evitando que sejamos lançados no para-brisa.

Em desenvolvimento de software, isso não é diferente. Temos diversas camadas, que muitas vezes nem imaginamos como realmente funcionam ou temos uma breve noção de como funcionam, não é mesmo?

Todo componente que temos podemos entender que ele faz parte da nossa **cadeia de suprimentos**, ou **supply chain**.

### O que é uma cadeia de suprimentos?

Quando estamos desenvolvendo uma aplicação e precisamos adicionar uma biblioteca para manipulação de datas por exemplo, podemos usar uma biblioteca popular do npm. Nesse ponto, temos nosso suprimento e é assim que funciona mais ou menos.

Primeiro, a biblioteca é hospedada no npm e mantida por desenvolvedores. Ela pode depender de outras bibliotecas menores, cada uma com seus próprios desenvolvedores e repositórios. 

Em seguida podemos adicionar essa biblioteca ao nosso projeto através do comando `npm install lib-data`. Quando executamos esse comando a biblioteca é baixada dos servidores do npm para ser utilizado em nosso projeto, e então podemos utilizar ela para desenvolver a aplicação. 

Finalmente, terminamos o desenvolvimento e vamos lançar o projeto no ambiente de produção onde será acessada pelos usuários. 

**IMPORTANTE** Estamos lançando o nosso código + o código do desenvolvedor da lib. 

Entendeu porque eu disse: "Não estamos desenvolvendo sozinhos, estou permitindo que terceiros contribuam com meu software"?

**O que faz parte da cadeia de suprimentos? Estamos cuidado dela?**

Quando desenvolvemos um software, incluímos diversos componentes como: serviços, bibliotecas de terceiros, APIs, infraestrutura de rede, hardware, software e muito mais em nossa supply chain. Cada um desses elementos pode impactar a qualidade e a segurança do nosso produto final.

### Refletindo

Agora, que sabemos o que é supply chain e o que faz parte dela, nosso software está realmente seguro? É confiável? Assim como em uma padaria, onde um ingrediente de má qualidade pode estragar o pão, no desenvolvimento de software, um componente inseguro ou ineficiente pode comprometer todo o sistema.

Quer saber como vou prevenir o meu container docker de um ataque direto no repositório? Semana que vem disponibilizarei esse laboratório com uma forma que vou dificultar a vida para essa vulnerabilidade. Sim, dificultar! como um virus que estamos tratando com antibiótico ele pode morrer ou voltar mais forte!

Enquanto isso, vamos lá verificar a qualidade e a segurança de cada parte do nosso software, e não vamos negligenciar nenhum detalhe por menor que pareça. Afinal, a segurança é feita em camadas e a eficiência do nosso produto final depende da integridade de toda a cadeia de suprimentos e não somente da gente.

