# Desafio Dio Criando a sua Própria Cena no Unity



**Projeto completo e abrangente para modificar um microgame no Unity:**



**Objetivo:** Modificar o microgame "Asteroids" para que as naves inimigas atirem em intervalos regulares.



**Recursos:**



- **Unity Editor**

- **Script C#**

  

### **Passos:**



**1. Crie um novo projeto do Unity.**

**2. Importe o pacote de ativos do microgame "Asteroids".**

**3. Crie um novo script chamado "EnemyShoot".**

**4. Adicione o seguinte código ao script "EnemyShoot":**



csharp



```csharp
using UnityEngine;
using System.Collections;

public class EnemyShoot : MonoBehaviour
{
    public GameObject bulletPrefab; // Prefab do projétil
    public float fireRate = 1f; // Taxa de tiro em segundos

    private float nextFireTime; // Próximo momento em que o inimigo pode atirar

    private void Start()
    {
        // Define o próximo momento em que o inimigo pode atirar
        nextFireTime = Time.time + fireRate;
    }

    private void Update()
    {
        // Verifica se é hora de atirar
        if (Time.time >= nextFireTime)
        {
            // Instancia um projétil
            Instantiate(bulletPrefab, transform.position, Quaternion.identity);

            // Define o próximo momento em que o inimigo pode atirar
            nextFireTime = Time.time + fireRate;
        }
    }
}
```



### **Recursos adicionais:**



- Documentação da API do Unity para Instantiate

  

- Tutorial da Unity sobre como criar e disparar projéteis





**5. Anexe o script "EnemyShoot" a cada nave inimiga.**



**6. Ajuste a taxa de tiro conforme desejado.**



**7. Salve e execute o jogo.**



**Resultado:** As naves inimigas agora atirarão em intervalos regulares.



**Recursos adicionais:**





Código Completo e Abrangente para Criando a sua Própria Cena no Unity



```plaintext
using UnityEngine;

public class SceneController : MonoBehaviour
{
    public GameObject[] objectsToSpawn;

    private void Start()
    {
        // Spawn the objects in the scene
        for (int i = 0; i < objectsToSpawn.Length; i++)
        {
            Instantiate(objectsToSpawn[i], transform.position, Quaternion.identity);
        }
    }
}
```



Este script pode ser anexado a um objeto na cena para gerar outros objetos quando a cena é carregada. Você pode especificar quais objetos deseja gerar na matriz `objectsToSpawn`.



#### Para usar este script:

1. Crie um novo objeto vazio na cena.
2. Anexe o script `SceneController` ao objeto.
3. Arraste e solte os objetos que deseja gerar na matriz `objectsToSpawn` no inspetor.
4. Salve a cena.

Quando a cena for carregada, o script `SceneController` gerará os objetos especificados na matriz `objectsToSpawn`.





**Código completo e abrangente para criar uma nova cena no Unity:**

csharp



```csharp
using UnityEngine;
using System.Collections;

public class SceneController : MonoBehaviour
{
    public string sceneName; // Nome da cena a ser carregada
    public float delay = 2f; // Atraso em segundos antes de carregar a cena

    private void Start()
    {
        // Carrega a cena após o atraso especificado
        StartCoroutine(LoadScene());
    }

    IEnumerator LoadScene()
    {
        yield return new WaitForSeconds(delay);

        // Carrega a cena especificada pelo nome
        SceneManager.LoadScene(sceneName);
    }
}
```



### **Como usar este script:**



1. Crie um novo objeto vazio na cena.
2. Anexe o script `SceneController` ao objeto.
3. No inspetor, defina o nome da cena que deseja carregar no campo `sceneName`.
4. Defina o atraso em segundos antes de carregar a cena no campo `delay`.
5. Salve a cena.

Quando a cena for carregada, o script `SceneController` carregará automaticamente a cena especificada após o atraso definido.



### **Recursos adicionais:**



- Documentação da API do Unity para SceneManager
- Tutorial da Unity sobre como carregar cenas
