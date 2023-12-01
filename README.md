# EDGECOMPUTING-COMPUTER-SYSTEMS

Uma breve descrição do problema de saúde abordado:
Dinamômetro é um aparelho utilizado para medir a intensidade da força. Essa intensidade pode ser mediada em quilograma-força ou em Newton. Essa definição casa muito bem com a sua utilização no dia a dia dos profissionais de fisioterapia que utilizam o aparelho para realizar testes de avaliação de força em seus pacientes.
Os testes de avaliação de força realizados com um dinamômetro permitem conhecer a capacidade muscular máxima e média de um grupo de membros, superiores ou inferiores. O que faz com que sua utilização seja útil não somente no campo da fisioterapia, mas também na musculação, preparação física e educação física.

Uma visão geral da solução proposta.
"A aplicação do dinamômetro é simples, mas poderosa. Utilizamos flex sensors no hand grip, que detectam a intensidade do aperto. Esses dados são processados pelo Arduino, convertidos em unidades de força e exibidos na tela lcd de maneira fácil de entender."

Instruções claras sobre como configurar e executar a aplicação.
Ao apertar o hand grip, o flex sensor colocado no hand grip gera uma angulação ao contrair, com base nesse ângulo é calculado a força da pessoa. Essa informação é valiosa para ajustar treinos e monitorar progresso de evolução.

Um link para a simulação do projeto no Tinkercad
https://www.tinkercad.com/things/gLZc6dnh5Pd-dinamometroo?sharecode=V3U_mu0J_j-zECpWLjrEeIM-_g075OBQfurAo6OIC2Y

Código Fonte:
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

// Definindo o valor inicial desejado
int valorInicial = 990;

void setup() { 
  pinMode(A0, INPUT);
  Serial.begin(9600);
  lcd.begin(16, 2); 
}

void loop() {
  int sensor = analogRead(A0);

  // Subtraindo o valor inicial e multiplica por 2 para ir de 2 em 2
  // Esse calculo é feito para aparecer os numeros em valores plausiveis para medição
  int valorExibido = (sensor - valorInicial) * 2;

  delay(400);
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("Valor da forca:");
  lcd.setCursor(0, 1);

  // Exibindo o valor ajustado com "kgs" ao lado
  lcd.print(valorExibido);
  lcd.print(" kgs");
  delay(400);
}
