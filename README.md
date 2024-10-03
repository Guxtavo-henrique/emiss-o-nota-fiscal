Emissão de Nota Fiscal de Serviço (NFS-e)
Este projeto consiste em uma página HTML com JavaScript que permite a leitura dos dados necessários para a emissão de uma Nota Fiscal de Serviço (NFS-e). A página realiza o cálculo dos impostos com base nos dados inseridos pelo usuário e gera a nota fiscal para exibição.

Código Fonte

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nota Fiscal de Serviço</title>
</head>
<body>
    <h1>Emissão de Nota Fiscal de Serviço (NFS-e)</h1>
    <form id="nfseForm">
        <label for="valorVenda">Valor da Venda:</label>
        <input type="number" id="valorVenda" name="valorVenda" required><br><br>
        
        <label for="itensVendidos">Itens Vendidos:</label>
        <textarea id="itensVendidos" name="itensVendidos" required></textarea><br><br>
        
        <label for="irpf">Porcentagem do IRPF:</label>
        <input type="number" id="irpf" name="irpf" required><br><br>
        
        <label for="pis">Porcentagem do PIS:</label>
        <input type="number" id="pis" name="pis" required><br><br>
        
        <label for="cofins">Porcentagem do COFINS:</label>
        <input type="number" id="cofins" name="cofins" required><br><br>
        
        <label for="inss">Porcentagem do INSS:</label>
        <input type="number" id="inss" name="inss" required><br><br>
        
        <label for="issqn">Porcentagem do ISSQN:</label>
        <input type="number" id="issqn" name="issqn" required><br><br>
        
        <button type="button" onclick="gerarNfse()">Gerar NFS-e</button>
    </form>
    
    <h2>Nota Fiscal de Serviço (NFS-e)</h2>
    <div id="notaFiscal"></div>
    
    <script>
        function calcularImpostos(valor, porcentagem) {
            return valor * (porcentagem / 100);
        }

        function gerarNfse() {
            const valorVenda = parseFloat(document.getElementById('valorVenda').value);
            const itensVendidos = document.getElementById('itensVendidos').value;
            const irpf = parseFloat(document.getElementById('irpf').value);
            const pis = parseFloat(document.getElementById('pis').value);
            const cofins = parseFloat(document.getElementById('cofins').value);
            const inss = parseFloat(document.getElementById('inss').value);
            const issqn = parseFloat(document.getElementById('issqn').value);

            const irpfValor = calcularImpostos(valorVenda, irpf);
            const pisValor = calcularImpostos(valorVenda, pis);
            const cofinsValor = calcularImpostos(valorVenda, cofins);
            const inssValor = calcularImpostos(valorVenda, inss);
            const issqnValor = calcularImpostos(valorVenda, issqn);

            const notaFiscal = `
                <p>Valor da Venda: R$ ${valorVenda.toFixed(2)}</p>
                <p>Itens Vendidos: ${itensVendidos}</p>
                <p>IRPF: R$ ${irpfValor.toFixed(2)}</p>
                <p>PIS: R$ ${pisValor.toFixed(2)}</p>
                <p>COFINS: R$ ${cofinsValor.toFixed(2)}</p>
                <p>INSS: R$ ${inssValor.toFixed(2)}</p>
                <p>ISSQN: R$ ${issqnValor.toFixed(2)}</p>
            `;

            document.getElementById('notaFiscal').innerHTML = notaFiscal;
        }
    </script>
</body>
</html>
