PALAVRA CHAVE 

UNITE

ANOTAÇÕES 
# HTML

HyperText 
Markup
Language


# CSS

Cascading
StyleSheet


const participante = {
  nome:"Gustavo Rezani",
  email:"gurezani@gmail.com",
  dataInscricao: new Date(2024, 0, 16, 19, 20),
  dataCheckIn: new Date(2024, 2, 4, 20, 22)
}

let participantes = [
  {
  nome:"Gustavo Rezani",
  email:"gurezani@gmail.com",
  dataInscricao: new Date(2024, 0, 16, 19, 20),
  dataCheckIn: new Date(2024, 2, 4, 20, 22)
}
]

//estrutura de repetição 
for(let participante of participantes) {
    output = output + criarNovoParticipante(participante)
 }



 let participantes = [
  {
    nome: "Gustavo Rezani",
    email: "gurezani@gmail.com",
    dataInscricao: new Date(2024, 0, 16, 19, 20),
    dataCheckIn: new Date(2024, 2, 4, 20, 22)
  },
  {
    nome: "Fernanda Silva",
    email: "fernanda.silva@example.com",
    dataInscricao: new Date(2023, 11, 5, 10, 15),
    dataCheckIn: new Date(2024, 1, 18, 12, 30)
  },
  {
    nome: "Ricardo Oliveira",
    email: "ricardooliveira@example.com",
    dataInscricao: new Date(2024, 1, 10, 14, 45),
    dataCheckIn: new Date(2024, 3, 1, 9, 10)
  },
  {
    nome: "Camila Santos",
    email: "camilasantos@example.com",
    dataInscricao: new Date(2024, 0, 22, 8, 0),
    dataCheckIn: new Date(2024, 2, 15, 17, 45)
  },
  {
    nome: "João Oliveira",
    email: "joao.oliveira@example.com",
    dataInscricao: new Date(2024, 1, 5, 16, 30),
    dataCheckIn: new Date(2024, 2, 20, 11, 20)
  },
  {
    nome: "Carolina Lima",
    email: "carolinalima@example.com",
    dataInscricao: new Date(2024, 0, 30, 11, 10),
    dataCheckIn: new Date(2024, 2, 10, 8, 5)
  },
  {
    nome: "Pedro Mendes",
    email: "pedromendes@example.com",
    dataInscricao: new Date(2024, 1, 15, 9, 30),
    dataCheckIn: new Date(2024, 3, 3, 14, 40)
  },
  {
    nome: "Marina Souza",
    email: "marinasouza@example.com",
    dataInscricao: new Date(2024, 0, 5, 13, 20),
    dataCheckIn: new Date(2024, 1, 25, 19, 15)
  },
  {
    nome: "Lucas Pereira",
    email: "lucaspereira@example.com",
    dataInscricao: new Date(2024, 1, 25, 17, 45),
    dataCheckIn: new Date(2024, 3, 5, 10, 30)
  },
  {
    nome: "Mariana Costa",
    email: "marianacosta@example.com",
    dataInscricao: new Date(2024, 0, 10, 10, 0),
    dataCheckIn: new Date(2024, 2, 5, 15, 20)
  }
];

const criarNovoParticipante = (participante) => {
  const dataInscricao = dayjs(Date.now())
  .to(participante.dataInscricao)
  
  let dataCheckIn = dayjs(Date.now())
  .to(participante.dataCheckIn)
  
  if(participante.dataCheckIn == null) {
    dataCheckIn = `
      <button
        data-email="${participante.email}"
        onclick="fazerCheckIn(event)"
      >
        Confirmar check-in
      <button>
    `
  }
  
  return `
  <tr>
    <td>
      <strong>
        ${participante.nome}
      </strong>
        <br>
        <small>
          ${participante.email}
        </small>
    </td>
    <td>${dataInscricao}</td>
    <td>${dataCheckIn}</td>
  </tr>
  `
}
const atualizarLista = (participantes) => {
 let output = ""
 
 for(let participante of participantes) {
    output = output + criarNovoParticipante(participante)
 }
 
 document
 .querySelector('tbody')
 .innerHTML = output
}

atualizarLista(participantes)

const adicionarParticipante = (event) => {
  event.preventDefault()

  const dadosDoFormulario = new FormData(event.target)

  const participante = {
    nome: dadosDoFormulario.get('nome'),
    email: dadosDoFormulario.get('email'),
    dataInscricao: new Date(),
    dataCheckIn: null
  }

  participante = [participante, ...participantes]
  atualizarLista(participantes)

}

















#HTML
<script src="https://cdn.jsdelivr.net/npm/dayjs@1/dayjs.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/dayjs@1/plugin/relativeTime.js"></script>
<script>dayjs.extend(window.dayjs_plugin_relativeTime)</script>
<script src="https://cdn.jsdelivr.net/npm/dayjs@1/locale/pt-br.js"></script>
<script>dayjs.locale('pt-br')</script>

<form onsubmit="adicionarParticipante(event)">
  <fieldset>
    <legend>inscrição</legend>

    <div>
      <input type="text"
      placeholder="Nome Completo"
      name="nome"
      >

      <input type="email"
      placeholder="Email"
      name="email"
      required
      >

      <button>
        REALIZAR INSCRIÇÃO
      </button>
    </div>
  </fieldset>
</form>


<table width="100%">
  <thead style="text-align: left">
    <tr>
      <th>Participante</th>
      <th>Data de inscrição</th>
      <th>Data do check-in</th>
    </tr>
  </thead>

  <tbody>
    
  </tbody>
</table>