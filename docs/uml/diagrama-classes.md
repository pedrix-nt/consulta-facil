classDiagram
    class Pessoa {
        -nome: str
        -idade: int
        -altura: float
        +__init__()
        +seApresentar()
    }

    class Aluno {
        -matricula: str
        +seApresentar()
    }

    class Professor {
        -disciplina: str
        +seApresentar()
    }

    class Paciente {
        -cpf: str
        -telefone: str
        +atualizarCadastro()
    }

    class ProfissionalSaude {
        -registro: str
        -especialidade: str
        +consultarAgenda()
    }

    class Administrador {
        -matricula: str
        +gerenciarVagas()
    }

    class SistemaCadastro {
        -pessoas: list
        +cadastrarPessoa()
        +listarPessoas()
        +buscarPessoa()
    }

    class Triagem {
        -respostas: list
        -classificacao: str
        +realizarTriagem()
    }

    class Especialidade {
        -nome: str
        -descricao: str
        +listarProfissionais()
    }

    class Agendamento {
        -data: str
        -horario: str
        -tipoVaga: str
        -status: str
        +confirmar()
        +cancelar()
    }

    Pessoa <|-- Aluno
    Pessoa <|-- Professor
    Pessoa <|-- Paciente
    Pessoa <|-- ProfissionalSaude
    Pessoa <|-- Administrador

    SistemaCadastro o-- Pessoa
    Paciente "1" --> "0..*" Agendamento
    ProfissionalSaude "1" --> "0..*" Agendamento
    Agendamento --> Especialidade
    Paciente "1" --> "0..*" Triagem
