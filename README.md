# Simulando-um-Ataque-de-Brute-Force-de-Senhas-com-Medusa-e-Kali-Linux
Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux

Relatório de Simulação: Ataque de Brute Force (Medusa)

Data: 23 de Março de 2026

Ferramentas: Kali Linux, Medusa

Objetivo: Demonstrar a vulnerabilidade de serviços com autenticação fraca e testar a eficácia de listas de usuários/senhas (wordlists).
1. Resumo Executivo

A atividade consistiu em realizar um ataque de força bruta (ou dictionary attack) contra o protocolo HTTP de um alvo específico. Utilizando a ferramenta Medusa no ambiente Kali Linux, foram testadas combinações de credenciais comuns para identificar falhas de segurança no controle de acesso.
2. Metodologia e Execução
A. Preparação do Ambiente

Para a simulação, foram criadas wordlists personalizadas contendo usuários e senhas comumente encontrados em configurações padrão ou de baixa complexidade.

    Criação da lista de usuários:
    Bash

    echo -e "user\nmsfadmin\nadmin\nroot" > users.txt

    Criação da lista de senhas:
    Bash

    echo -e "123456\npassword\nqwerty" > pass.txt

B. Execução do Ataque

O comando utilizado para iniciar a verificação foi:
medusa -h [IP_ALVO] -U users.txt -P pass.txt -M http

Parâmetros utilizados:

    -h: Define o endereço IP do host alvo.

    -U: Indica o arquivo com a lista de nomes de usuários.

    -P: Indica o arquivo com a lista de possíveis senhas.

    -M: Especifica o módulo do protocolo (neste caso, HTTP).

3. Análise de Resultados

Durante a execução, o Medusa realiza tentativas sequenciais cruzando todos os itens de users.txt com pass.txt.

    Cenário de Sucesso: Se o serviço alvo aceitar uma das combinações (ex: admin / password), a ferramenta interrompe o processo para aquele usuário e exibe a credencial válida em destaque.

    Cenário de Falha: Caso nenhuma combinação seja válida, o log indicará "0 credentials found".

4. Recomendações de Segurança (Mitigação)

Com base no sucesso deste tipo de ataque, as seguintes medidas são fundamentais para proteger sistemas:

    Políticas de Senhas Fortes: Implementar exigência de caracteres especiais, números e letras maiúsculas/minúsculas.

    Bloqueio de Conta (Account Lockout): Configurar o sistema para bloquear o acesso após 3 ou 5 tentativas falhas consecutivas.

    Autenticação de Dois Fatores (2FA): Mesmo que a senha seja descoberta, um segundo fator impede o acesso não autorizado.

    Alteração de Credenciais Padrão: Nunca manter usuários como admin, root ou msfadmin com senhas de fábrica.

    Nota de Estudo: Este relatório foi gerado para fins estritamente educacionais e laboratoriais. O uso dessas técnicas em sistemas sem autorização expressa é ilegal.
