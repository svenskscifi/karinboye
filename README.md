# karinboye
Training GPT-2 for generating Karin Boye Poems

In this repository you can find files and links connected to the project "Ammaseus Horisont" (www.svenskscifi.se/ammaseushorisont.html), where Open AI:s 355 miljon parameter GPT-2 pretrained model  has been retrained to generate Swedish Poems in the style of Karin Boye. Due to se large size of the GPT2 repository the larger datasets and the trained model, not all files are uploaded on this repository, but links are provided below.

Shortly, the GPT-2 model, especielly the GPT2-simple implementation, which can be find here (https://github.com/minimaxir/gpt-2-simple/) was used, and retrained in four steps (see below). All training has taken place on google cloud computing, with a standard GPU setting using an NVIDIA Tesla K80 GPU machine. The training rate was set to default for the first two steps, and set to a slower rate for the last two.

# Step 1

Training about 20 000 epochs on generic swedish texts (trainingdata 1) taken from Swedish Wikipedia and Svenska Språkinstitutet. The following datasets has been used:


# Step 2

After this the network was directly trained a smaller dataset of selected swedish literature from Project Runeberg (trainingdata 2), see "listoftrainingdata.txt" for a full list of selected works or the trainingdata2.txt for a combined textfile with all texts.

After 5000 epochs, the network generates swedish text like:

  	Han blev nästan sällan värkande, och fällde en man, som rörde sig in i den myckenhet, 
  	att han skulle kunna vässa spelmännen vid detta rum.

And after training the network for 20 000 epochs (which took about 17 hours), the network generates text like:

	Hör! Nu säger vi så: det är en skugga, en frisk och djupt dundrande, 
  	den är bara som en backe, ingen kan släcka det, och du behagar endast säga mer.


# Step 3

The network was then trained on a set of selected swedish poems (trainingdata3.txt), for 2000 cycles.


# Step 4

And finally the network was trained only on Karin Boye Poems (trainingdata4.txt), for 2000 cycles.
Example of results during this phase are shown below.

500 epochs

  	Du blommar och guld, guld 
  	Väntar på långt innan mörker 
  	och stelnad känner du döden. 

1 000 epochs

	Vacker är måsarna, 
  	lösta från resorna
  	av himlafurstarnas ängel.

2 000 epochs

	Jag ville veta, vad som väntade
       	de döda har sökt oss
       	i sömn låg vi hemma. 
  	Ammaseus horisont 
  	Ammaseus Horisont
  
  
  
  
 More example of generated poems, can be found in the textfile (exampleresults.txt).



