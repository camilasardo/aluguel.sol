# aluguel.sol
contrato de aluguel em blockchain

pragma solidity 0.5.12; 
//pausa para um comentário

contract Aluguel { 
    string public locatario; 
    string public locador; 
    uint256 private valor; 
    uint constant numeromaximolegaldealugueisparamulta = 3;

constructor(string memory nomeLocador, string memory nomeLocatario, uint256 valorDoAluguel) public{
    locador = nomeLocador; 
    locatario = nomeLocatario; 
    valor = valorDoAluguel;
}

function valorAtualDoAluguel() public view returns (uint256) {
    return valor;
}

function simulaMulta( uint256 mesesRestantes,
                uint256 totalMesesContrato)
public
view
returns(uint256 valorMulta) {
    valorMulta = valor*numeromaximolegaldealugueisparamulta;
    valorMulta = valorMulta/totalMesesContrato;
    valorMulta = valorMulta*mesesRestantes;
    return valorMulta;
}
    function reajustaAluguel(uint256 percentualReajuste) public {
        uint256 valorDoAcrescimo = 0;
        valorDoAcrescimo = ((valor*percentualReajuste)/100);
        valor = valor + valorDoAcrescimo;
    }
}
