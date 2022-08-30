# AlgoritmoHierarquico

Algoritmo Hierárquico para uma análise de aprendizado de máquina.<br><br>
<b>Escolha do dataset</b><br>

Dataset: Lymphography Data Set<br>
Número de exemplos: 148<br>
Número de atributos: 18<br>
Classes: 4 (normal find, metastases, malign lymph, fibrosis)<br><br>

<b>Análise exploratória:</b><br>

Foram plotados os atributos par-a-par e não foi identificado uma combinação no qual a classe se destacasse linearmente das demais.<br>

Classificadores utilizados: (Hierarquia apenas nos classificadores Lineares)<br>
 
Hierarquia aplicada em: Classe de maior predominância para menor predominância na ordem [2,3,4,1].
 
Linear Discriminant Analysis - Após a Definição dos labels e features foi desenvolvida uma função. A função define a hierarquia das classes a partir da classe com a maior presença no dataset a dividindo do resto. Após isso o dataset foi tratado como binário entre classe com maior predominância(que no nosso dataset é a classe 2) e resto. 
Após isso foram criados dois vetores para no fim da execução armazenar os labels originais (orgLabels) e os features restantes (restFeatures)  que em tese  não pertencerão  a classe 2.
Após isso de fato começa a implementação de classificação, defini os K-folds em 5 partes para o treinamento. Transformei as novas labels em “np.array” pois sem isso o algoritmo não consegue trabalhar em cima dos valores.
A partir daqui começou nossa grande estrutura de repetição que aplicava o processo de classificação, utilizando os splits antes definidos e definindo os conjuntos de treinamento e teste
Foram criadas as variáveis “certas” e “todas” para no fim ser feita a validação.
Defini o modelo(LinearDiscriminantAnalysis()) e apliquei o comando .fit, e após isso foram feitas as predições no conjunto de teste. O próximo passo foi a definição da nossa próxima estrutura de repetição.
 A variável “j” não poderia ser maior que o tamanho do conjunto de teste, dentro desse for foram feitas as verificações das predições com as labels. Caso a predição fosse idêntica a label era feita uma incrementação da variável “certas” e a cada loop era feito um incremento da variável “todas”. Caso não houvesse igualdade na predição da classe era adicionado aos 2 vetores previamente declarados os valor e a label original daquele objeto a partir de seu número do index. Para a finalidade de no final deste for poder ser usado na próxima chamada de função.
Por fim dessa grande estrutura de repetição se fazia o cálculo da acurácia. Printa-se a acurácia e quantos elementos restam para ser classificados.
Para a finalização do nosso problema, é necessário a verificação do tamanho restante de rótulos originais, fazendo assim uma simples verificação e número. Caso seja maior que zero, nossa função não terá terminado.
Levando essa informação como verdadeira, temos  nossos vetores de features e labels restantes sendo convertidos para np.array para se obter uma nova chamada de função.
Por fim a função modeloLDA é chamada recursivamente utilizando os dois vetores mencionados acima até que não se tenham mais elementos para serem classificados
A acurácia obtida nas recursividades foram: acurácia 79.31 restou 62 exemplos ,
acurácia 91.67 restou 11 exemplos, acurácia 50.00 restou 7 exemplos, acurácia 0.00 restou 5 exemplos, acurácia 100.00 restou 0 exemplos 
 
 	
 
Gaussian Naive Bayes-  95% da implementação deste classificador é semelhante a aplicada no modelo acima as duas diferenças presentes são a mudança de função, agora chamada “modeloGaussiana”  e o classificador utilizados GaussianNB()
 
Definiu-se duas vezes os features e labels no inicio do programa para que não houvesse interferência nos dois modelos aplicados no trabalho.
Obs: o Algoritmo de folds aplicado a Gaussiana apresentou um alerta quando na verificação final “if(len(orgLabels)>0):” o valor maior que 0 não deixava de rodar grande parte do programa, porém para evitar o alerta final foi alterado o valor para “>1”, eliminando por completo o alerta final sem comprometer o algoritmo.
A acurácia obtida nas recursividades foram: acurácia 86.21 restou 40 exemplos, 
acurácia 100.00 restou 10 exemplos, acurácia 0.00 restou 6 exemplos ,
acurácia 0.00 restou 1 exemplos 

