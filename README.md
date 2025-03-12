- 👋 Hi, I’m @sani239
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
sani239/sani239 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
using UnityEngine;

public class PlayerMovement : MonoBehaviour
{
    public float moveSpeed = 5f;
    public float jumpHeight = 2f;
    private Rigidbody rb;

    void Start()
    {
        rb = GetComponent<Rigidbody>();
    }

    void Update()
    {
        float moveX = Input.GetAxis("Horizontal");
        float moveZ = Input.GetAxis("Vertical");

        Vector3 movement = new Vector3(moveX, 0f, moveZ) * moveSpeed * Time.deltaTime;
        transform.Translate(movement, Space.World);

        if (Input.GetKeyDown(KeyCode.Space)) // Jumping
        {
            rb.AddForce(Vector3.up * jumpHeight, ForceMode.Impulse);
        }
    }
}using UnityEngine;

public class PlayerMovement : MonoBehaviour
{
    public float moveSpeed = 5f;
    public float jumpHeight = 2f;
    private Rigidbody rb;

    void Start()
    {
        rb = GetComponent<Rigidbody>();
    }

    void Update()
    {
        float moveX = Input.GetAxis("Horizontal");
        float moveZ = Input.GetAxis("Vertical");

        Vector3 movement = new Vector3(moveX, 0f, moveZ) * moveSpeed * Time.deltaTime;
        transform.Translate(movement, Space.World);

        if (Input.GetKeyDown(KeyCode.Space)) // Jumping
        {
            rb.AddForce(Vector3.up * jumpHeight, ForceMode.Impulse);
        }
    }using UnityEngine;

public class GunScript : MonoBehaviour
{
    public GameObject bulletPrefab;
    public Transform shootPoint;
    public float bulletSpeed = 10f;

    void Update()
    {
        if (Input.GetMouseButtonDown(0)) // Left click to shoot
        {
            ShootBullet();
        }
    }

    void ShootBullet()
    {
        GameObject bullet = Instantiate(bulletPrefab, shootPoint.position, shootPoint.rotation);
        Rigidbody rb = bullet.GetComponent<Rigidbody>();
        rb.velocity = shootPoint.forward * bulletSpeed;
    }
}void Start()
{
    Application.targetFrameRate = 120; // Set FPS to 120
}QualitySettings.SetQualityLevel(5); // 5 represents highest qualityusing Firebase.Auth;
using UnityEngine;

public class LoginManager : MonoBehaviour
{
    FirebaseAuth auth;

    void Start()
    {
        auth = FirebaseAuth.DefaultInstance;
    }

    public void SignIn(string email, string password)
    {
        auth.SignInWithEmailAndPasswordAsync(email, password).ContinueWith(task => 
        {
            if (task.IsCompleted)
            {
                Debug.Log("Logged in successfully");
            }
            else
            {
                Debug.LogError("Login failed");
            }
        });
    }
}using UnityEngine;
using UnityEngine.UI;

public class SettingsMenu : MonoBehaviour
{
    public Slider musicSlider;
    public Slider graphicsSlider;

    void Start()
    {
        musicSlider.onValueChanged.AddListener(ChangeMusicVolume);
        graphicsSlider.onValueChanged.AddListener(ChangeGraphicsQuality);
    }

    void ChangeMusicVolume(float volume)
    {
        AudioListener.volume = volume; // Set music volume
    }

    void ChangeGraphicsQuality(float quality)
    {
        QualitySettings.SetQualityLevel((int)quality); // Adjust graphics quality
    }
}using UnityEngine;

public class GameManager : MonoBehaviour
{
    public GameObject playerPrefab;
    public Transform spawnPoint;

    void Start()
    {
        SpawnPlayer();
    }

    void SpawnPlayer()
    {
        Instantiate(playerPrefab, spawnPoint.position, spawnPoint.rotation);
    }

    public void EndGame()
    {
        // Handle end of game, show game over screen
        Debug.Log("Game Over");
    }
}
