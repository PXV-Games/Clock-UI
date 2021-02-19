using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class ClockUI : MonoBehaviour
{

    public class Clock : MonoBehaviour
    {
        public Transform minuteHandTransform;
        public Transform hourHandTransform;
        private float day;
        public float realSecondsPerGameDay = 3600.0f;
        public float fullRotationsPerGameDay = 720.0f;
        public float hoursPerDay = 24.0f;
        public float minutesPerHour = 60.0f;

        private void Update()
        {
            day += Time.deltaTime / realSecondsPerGameDay;

            float dayNormalized = day % 1.0f;

            hourHandTransform.eulerAngles = new Vector3(0, 0, -dayNormalized * fullRotationsPerGameDay);
            minuteHandTransform.eulerAngles = new Vector3(0, 0, -dayNormalized * fullRotationsPerGameDay * hoursPerDay);
        }
    }
}
