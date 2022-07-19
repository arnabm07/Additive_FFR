# Additive_FFR
Additive Function-on-Function Regression (AFF-PC)

README FILE

Additive Function-on-Function Regression (AFF-PC)
by Janet S. Kim, Ana-Maria Staicu, Arnab Maity, Raymond J. Carroll, and David Ruppert <br>
Nov/07/2016 <br>

CONTENTS:

I.	datagenALL.r
II.	AFFfit.r
III.	AFFinf.r
IV.	ex_AFFfit.r
V.	ex_AFFinf.r

PACKAGE:  MASS, Matarix, refund, mgcv


DESCRIPTION:

I. datagenALL.r
Functions used to simulate data sets.
(i) 	X: create functional covariate with/without errors
(ii) 	G1 - G5: bivariate functions of "X" and "s"
	Int_G: Int_s G{X(s),s}ds
(iii)	Phi: generate orthogonal basis functions
(iv)	Int_F: Compute int_s F{X(s),s,t}ds
	          	linear case 		if model_opt = 1
		simple non-lineaer case 	if model_opt = 2
		complex non-linear case	if model_opt = 3
(v) 	build.AR: build AR(1) covariance matrix for random errors
	Error_resp: generate random errors for response
(vi) 	datagen: generate training and test set
		Xfull/Wfull		true/noisy covariate; defined on dense and regular grids
		Xeval/Weval		true/noisy covariate; defined on sparse and irregular grids 
		Error.full/Error.eval	random errors defined on regular dense/sparse grids
		Int_Ffull			Int_s F{X(s),s,t}ds
		Yfull/Yeval		Int_Ffull + Error.full/Int_Ffull + Error.eval
(vii)	BS.datagen: generate bootstrap data set


II. AFFfit.r
AFF() function used to fit the following models:
		AFF-PC 			if fit_opt = "AFF-PC"
		FLM 			if fit_opt = "FLM"
		AFF-S 			if fit_opt = "AFF-S" (spline-based model proposed by Scheipl et al. 2015)
		
		output:
		Yfit			fitted curves obtained based on training data
		Ypred			predicted curves obtained from test data
		RMSPE_in			in-sample prediction error
		RMSPE_out 		out-of-sample prediction error


III. AFFinf.r
Functions used to perform out-of-sample predition inference
(i) Main functions
	Pred_inf: perform out-of-sample prediction inference, and provide the following lists
		Yfit			fitted curves obtained from training data
		Ypred			predicted curves obtained from test data
		VarYp			marginal prediction variance
		ACPp			average covarage probabilities at nominal levels of 0.85, 0.90, 0.95
	AFF_bs: compute model-based prediction variance based on a bootstrap sample, and provide the following lists
		Ypred			predicted curves from bootstrap sample
		VarYp			model-based variance when a new covariate function is given
(ii) Ancillary functions
	G: estimate covariance matrix and its inverse, and provide the following lists
	var.psi: compute varaince of predicted scores when p=q; covariance of predicted scores when p!=q
	model.Var: calculate model-based variance using formula (9) in the main paper
	ACP: calculate average coverage probability


IV. ex_AFFfit.r
Example of how to use "datagenALL.r" and "AFFfit.r".


V. ex_AFFinf.r
Example of how to use "datagenALL.r" and "AFFinf.r".



