Regra de Nomenclatura para Binários do Carregador Rockchip

Regra Geral: Independentemente de ser um módulo único ou um carregador integrado, a convenção de nomenclatura é:

[chip]_[módulo]_[recurso]_[versão].[sufixo]

* **chip:** Nome do chip ou família de chips, obrigatório, consistente com os nomes em todos os drivers do kernel/uboot. Convenções de nomenclatura específicas não são discutidas aqui. Minúsculas.

* **módulo:** Nome do módulo, obrigatório, como loader, ddr, miniloader, usbplug, bl3x, tee, tee_ta. Minúsculas.

* **recurso:** Recurso do módulo, opcional, múltiplos recursos permitidos. Exemplos incluem frequência de uso da DDR, suporte para uma DDR específica ou opções especiais para o miniloader. Minúsculas.

* **versão:** Informações da versão, obrigatórias, formatadas como [v1.00,], 0.xx antes do lançamento oficial, 1.00 e posteriores após o lançamento oficial. Minúsculas.

* **sufixo:** Extensão do arquivo, obrigatória. O padrão após a compilação é .bin, mas .elf também é possível. O arquivo resultante será um arquivo .img, em minúsculas.

O conector usa um sublinhado "_".

Por exemplo:
O arquivo fornecido pelo módulo ddr
rk3228_ddr3_800MHz_v1.06.bin

Regras Especiais:

1. Nomenclatura do carregador resultante:
    
    >[!loader]
    >Um carregador resultante da fusão de ddrbin, usbplug e miniloader, utilizável na ferramenta de atualização do Windows RK;
    
    >[!ubootloader]
    >Um carregador resultante da fusão de ddrbin, usbplug e U-Boot, utilizável na ferramenta de atualização do Windows RK;
    
    >[!idbloader]
    >Um binário resultante da fusão de ddrbin e do carregador de primeiro nível (miniloader ou uboot) no formato IDB, usado diretamente para gravação na área IDB;
    
    >[!Nota]
    >O nome do miniloader indica apenas a saída binária da compilação do projeto do miniloader e não será usado no carregador integrado;

2. Definição da versão do carregador integrado:
    
        vx.yy.zzz
        
    v: Significa versão, sempre use este caractere, em minúsculas
    
    x.yy: Número da versão do arquivo fornecido pelo ddr, em minúsculas
    
    zzz: [1] é o número da versão do arquivo fornecido pelo miniloader, em minúsculas, sem o ponto.
         [2] é o número da versão fornecido pelo uboot.

3. Se o uso de minúsculas causar ambiguidade, use maiúsculas.
    
    Por exemplo, GB para ddr não pode ser escrito como gb.
        
        Exemplo: O carregador combinado tem o seguinte nome:
        rk3328_loader_v1.03.106.bin
        
    1.03 é o número da versão da DDR, v1.03.
    
    106 é o número da versão do miniloader, v1.06, sem o ponto.
