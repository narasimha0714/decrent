# decrent
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.EventSystems;
public class ComparisonStepper : MonoBehaviour,IPointerClickHandler {

	public Text StepperText,maxText,minText;
	public float steppercount;
	[SerializeField]
	int id;
	public AR_AudioSourseManagerScript sounde;
	// Use this for initialization
	void Start () {
		
	}

	#region IPointerClickHandler implementation

	public void OnPointerClick (PointerEventData eventData)
	{
		OnMouseDown1 ();
	}

	#endregion
	
	// Update is called once per frame
	void OnMouseDown1 () 
	{
		steppercount = float.Parse (StepperText.text);	
		if (id == 0)
		{
			if (this.name == "rt")
			{
				if (steppercount < float.Parse (maxText.text)-1)
				{
					steppercount++;
					StepperText.text = steppercount + "";
					sounde.sfxSource [0].Play ();
				}
				
			}
			else if (this.name == "lt")
			{
				if (steppercount >1)
				{
					steppercount--;
					StepperText.text = steppercount + "";
					sounde.sfxSource [0].Play ();
				}

			}
		}
		else 	if (id == 1)
		{
			if (this.name == "rt")
			{
				if (steppercount < 9)
				{
					steppercount++;
					StepperText.text = steppercount + "";
					sounde.sfxSource [0].Play ();
				}

			}
			else if (this.name == "lt")
			{
				if (steppercount >float.Parse (minText.text)+1)
				{
					steppercount--;
					StepperText.text = steppercount + "";
					sounde.sfxSource [0].Play ();
				}

			}
		}

		ComparisonManager.Instance.SetFirstFraction ();
		ComparisonManager.Instance.SetSecondFraction ();
	}
}
