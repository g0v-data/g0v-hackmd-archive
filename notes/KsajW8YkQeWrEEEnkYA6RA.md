# automoving
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
public class MainMoving : MonoBehaviour { // Use this for initialization void Start () { } public float dx; public Vector3 size; // Update is called once per frame void Update () { if (Input.GetKey (KeyCode.W)) transform.Translate (0, 0, dx); else if (Input.GetKey (KeyCode.S)) transform.Translate (0, 0, -dx); if (transform.position.x > size.x / 2 || transform.position.x < size.x / (-2)) transform.Translate (-transform.position.x, transform.position.y, transform.position.z); if (transform.position.y > size.y / 2 || transform.position.y < size.y / (-2)) transform.Translate (transform.position.x, -transform.position.y, transform.position.z); if (transform.position.z > size.z / 2 || transform.position.z < size.z / (-2)) transform.Translate (transform.position.x, transform.position.y, -transform.position.z); } }
