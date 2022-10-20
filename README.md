Hospedando um Jogo Unity baseado em WebGL no GitHub: https://alfredo1995.github.io/simulador-direcao-unity/

<br>

Hospedando jogo no github 

    
    1) Edit > Projetc Settings > Player > Resolutions and Representation > marcar a caixa > Run in Background
    
    2) Edit > Projetc Settings > Player > Publishing Settings > Compression format > marcar a caixa > Dissabled
    
    3) File > Build Settings > Build and Run > Criar uma nova pasta > Selecionar a pasta para ser executador a build
    
    4) Github > New Repostory > Dar o nome do Projeto > Create Repository > Uploading and existing file
    
    5) Acessar a nova pasta criada no passo 3 > copiar todos os arquivos e arrastar para o Uploading and existing file > commit changes
    
    6> config > page > branch none > trocar para main > save
    
    
Hospedando jogo no Itch.io
    
    
    1) Edit > Projetc Settings > Player > Resolutions and Representation > marcar a caixa > Run in Background
    
    2) Edit > Projetc Settings > Player > Publishing Settings > Compression format > marcar a caixa > Dissabled
    
    3) Unity 3.0 > Intal > Version da unity do jogo >  Add modulos > webglbuild support
    
    4) File > Build Settings > Build and Run > Criar uma nova pasta > Selecionar a pasta para ser executador a build
    
    5) acessar o site https://itch.io > Perfil > Upload new Project > Der o nome ao projeto  > Kind of project > Selecione > HTML you have zip
    
    6 ) Uploads > Upload files > Acessa a nova pasta criada > selecione todos os arquivos > compactar todos os arquivo em um so zip > 
    
    7 > Apos o upload > Selecione a opção > This file will be played in the browser  >  opcional mudar a Emedend point ( resolução da tela )
    
    
Hospedando jogo android

    Download > Unity Remote 5
    
    Ativar modo Desenvolvedor do Celular

    Edit > Project Setting > Player > Publishing Settings > KeyStore Manager > Create New > AnyWhere
    
    File > Build Setting > Android > Rund dive > Select You Phone > Build and Run > Selecet You Key;

Ball Controller Accelerometer

        using UnityEngine;

        public class Example : MonoBehaviour
        {
            // Move object using accelerometer
            float speed = 10.0f;

            void Update()
            {
                Vector3 dir = Vector3.zero;

                // eixo de aceleração do dispositivo mapeamento as coordenadas do jogo:        
                //  1) Plano XY do dispositivo é mapeado no plano XZ
                //  2) rotacionado 90 grau em torno eixo Y
                dir.x = -Input.acceleration.y;
                dir.z = Input.acceleration.x;

                // vetor de aceleração do grampo p/ esfera
                if (dir.sqrMagnitude > 1)
                    dir.Normalize();

                // Movendo-se a 10 metros por segundo em vez de 10 metros por quadro...
                dir *= Time.deltaTime;

                // Move object
                transform.Translate(dir * speed);
            }
        }
        
        
  <br>      
        
Ball Controll Gyro


        using UnityEngine;
        using UnityEngine.UI;

        public class InputGyroExample : MonoBehaviour
        {
            //Classe do giroscópio p/ visualizar a orientação no espaço do dispositivo.
            
            //Sensores subjacentes usados para população de dados:
            Gyroscope m_Gyro;

            void Start()
            {
                //configuração e habilitação do giroscópio
                m_Gyro = Input.gyro;
                m_Gyro.enabled = true;
            }

        //Função, confirindo a interface do usuário
            void OnGUI()
            {
                //Output the rotation rate, attitude and the enabled state of the gyroscope as a Label
                GUI.Label(new Rect(500, 300, 200, 40), "Gyro rotation rate " + m_Gyro.rotationRate);
                GUI.Label(new Rect(500, 350, 200, 40), "Gyro attitude" + m_Gyro.attitude);
                GUI.Label(new Rect(500, 400, 200, 40), "Gyro enabled : " + m_Gyro.enabled);
            }
        }
