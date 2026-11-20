classDiagram

class Pessoa {
    -String nome
    -int idade
    -double altura
    +Pessoa(nome, idade, altura)
    +getNome()
    +getIdade()
    +getAltura()
    +seApresentar()
}

class Paciente {
    -LocalDate dataNascimento
    -String cpf
    -String sexo
    -String nomeMae
    -String telefone
    -String email
    -String endereco
    +Paciente()
    +atualizarCadastro()
    +consultarHistorico()
    +realizarTriagem()
}

class ProfissionalSaude {
    -String cpf
    -LocalDate dataNascimento
    -String sexo
    -String registro
    -String cargo
    -String telefone
    -String email
    -String endereco
    +ProfissionalSaude()
    +consultarAgenda()
    +listarEspecialidades()
}

class Administrador {
    -String cpf
    -LocalDate dataNascimento
    -String sexo
    -String telefone
    -String email
    -String matricula
    +Administrador()
    +gerenciarSistema()
    +gerenciarProfissionais()
    +gerenciarVagas()
}

class SistemaCadastro {
    -List~Pessoa~ pessoas
    +cadastrarPessoa()
    +listarPessoas()
    +buscarPessoa()
    +atualizarPessoa()
    +excluirPessoa()
}

class Triagem {
    -int id
    -LocalDate data
    -List~String~ respostas
    -String observacoes
    +registrarRespostas()
    +consultarTriagem()
}

class Especialidade {
    -int id
    -String nome
    -String descricao
    +listarProfissionais()
}

class UnidadeSaude {
    -int id
    -String nome
    -String endereco
    -String telefone
    +adicionarProfissional()
    +listarProfissionais()
    +consultarVagas()
}

class HorarioDisponivel {
    -int id
    -LocalDate data
    -LocalTime horario
    -int vagasComuns
    -int vagasPreferenciais
    +consultarDisponibilidade()
    +reservarVaga()
    +liberarVaga()
}

class Agendamento {
    -int id
    -LocalDate data
    -LocalTime horario
    -String tipoVaga
    -String status
    +confirmar()
    +cancelar()
    +consultarAgendamento()
}

Pessoa <|-- Paciente
Pessoa <|-- ProfissionalSaude
Pessoa <|-- Administrador

SistemaCadastro o-- Pessoa

Paciente "1" --> "0..*" Triagem : realiza
Paciente "1" --> "0..*" Agendamento : solicita

ProfissionalSaude "1" --> "0..*" Agendamento : atende
ProfissionalSaude "*" --> "1..*" Especialidade : possui

UnidadeSaude "1" o-- "0..*" ProfissionalSaude : possui
UnidadeSaude "1" o-- "0..*" HorarioDisponivel : disponibiliza

HorarioDisponivel "1" --> "0..*" Agendamento : recebe
Agendamento "*" --> "1" Especialidade : corresponde a
Agendamento "*" --> "1" UnidadeSaude : acontece em

Administrador ..> SistemaCadastro : gerencia
