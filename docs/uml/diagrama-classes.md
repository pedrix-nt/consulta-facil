classDiagram
    class Pessoa {
        -nome: str
        -idade: int
        -altura: float
        +__init__()
        +seApresentar()
    }

    class Paciente {
        -cpf: str
        -telefone: str
        -endereco: str
        +__init__()
        +seApresentar()
        +atualizarCadastro()
    }

    class ProfissionalSaude {
        -registro: str
        -cargo: str
        +__init__()
        +seApresentar()
        +consultarAgenda()
    }

    class Administrador {
        -matricula: str
        +__init__()
        +seApresentar()
        +gerenciarSistema()
    }

    class SistemaCadastro {
        -pessoas: list
        +cadastrarPessoa()
        +listarPessoas()
        +buscarPessoa()
    }

    class Triagem {
        -data: str
        -respostas: list
        -observacoes: str
        +registrarRespostas()
        +consultarTriagem()
    }

    class Especialidade {
        -id: int
        -nome: str
        -descricao: str
        +listarProfissionais()
    }

    class UnidadeSaude {
        -id: int
        -nome: str
        -endereco: str
        +listarProfissionais()
        +consultarVagas()
    }

    class HorarioDisponivel {
        -data: str
        -horario: str
        -vagasComuns: int
        -vagasPreferenciais: int
        +consultarDisponibilidade()
        +atualizarVagas()
    }

    class Agendamento {
        -id: int
        -data: str
        -horario: str
        -tipoVaga: str
        -status: str
        +confirmar()
        +cancelar()
        +consultarAgendamento()
    }

    Pessoa <|-- Paciente
    Pessoa <|-- ProfissionalSaude
    Pessoa <|-- Administrador

    SistemaCadastro o-- Pessoa
    Paciente "1" --> "0..*" Triagem
    Paciente "1" --> "0..*" Agendamento
    ProfissionalSaude "1" --> "0..*" Agendamento
    ProfissionalSaude "*" --> "1" Especialidade
    UnidadeSaude "1" --> "0..*" ProfissionalSaude
    UnidadeSaude "1" --> "0..*" HorarioDisponivel
    HorarioDisponivel "1" --> "0..*" Agendamento
    Agendamento "*" --> "1" Especialidade
