# karinboye
Training GPT-2 for generating Karin Boye Poems

In this repository you can find files and links connected to the project <a href="http://www.svenskscifi.se/ammaseus.html">Ammaseus Horisont</a>, where Open AI:s pretrained 355 M parameter GPT-2 model has been retrained to generate Swedish Poems in the style of Karin Boye. The GPT-2 model was published in the paper <a href="https://d4mucfpksywv.cloudfront.net/better-language-models/language-models.pdf">Language Models are Unsupervised Multitask Learners</a>, (Radford et al., 2019), and a full repository with runable code and models from that paper can be found here: https://github.com/openai/gpt-2

Due to the size of some of the datasets and the trained model, not all files are uploaded on this repository, but instead links to the files are provided below.

Shortly the pretrained GPT-2 model was retrained in four steps (see below). All training has taken place on google cloud computing, with a standard GPU setting using an NVIDIA Tesla K80 GPU machine. The training rate was set to default for the first two steps, and set to a slower rate for the last two.

# Step 1

Training about 20 000 epochs on generic swedish texts from Swedish Wikipedia, corresponding to approximatly 10 GB of text. A compressed xml dump can be downloaded from Svenska Språkbanken at: <a href="https://spraakbanken.gu.se/en/resources/wikipedia-sv">Wikipedia-sv</a>


# Step 2

After this the network was directly trained on a smaller dataset of selected swedish literature from <a href="http://runeberg.org">Project Runeberg</a> (<i>Trainingdata2.txt</i>), approximatly 90 MB of text. See <a href="https://github.com/svenskscifi/karinboye/blob/master/listoftrainingdata2.txt">listoftrainingdata2.txt</a> for a full list of the selected works. The full textfile with all combined works can be downloaded here: <a href="Trainingdata2.txt">Trainingdata2.txt</a>

After 5000 epochs, the network generates swedish text like:

  	Han blev nästan sällan värkande, och fällde en man, som rörde sig in i den myckenhet, 
  	att han skulle kunna vässa spelmännen vid detta rum.

And after training the network for 18 000 epochs, the network generates text like:

	Hör! Nu säger vi så: det är en skugga, en frisk och djupt dundrande, 
  	den är bara som en backe, ingen kan släcka det, och du behagar endast säga mer.


# Step 3

The network was then trained on a set of selected swedish poems <a href="https://github.com/svenskscifi/karinboye/blob/master/Trainingdata3.txt">Trainingdata3.txt</a>, for 2000 epochs. A list of the selected works can be found in <a href="https://github.com/svenskscifi/karinboye/blob/master/listoftrainingdata3.txt">listoftrainingdata3.txt</a>


# Step 4

And finally the network was trained only on Karin Boye Poems <a href="https://github.com/svenskscifi/karinboye/blob/master/Trainingdata4.txt">Trainingdata4.txt</a>, for 2000 epochs.
Example of results during this phase are shown below. A list of the selected works can be found in <a href="https://github.com/svenskscifi/karinboye/blob/master/listoftrainingdata4.txt">listoftrainingdata4.txt</a>


500 epochs

  	Du blommar och guld, guld 
  	Väntar på långt innan mörker 
  	och stelnad känner du döden. 

1 000 epochs

	Vacker är måsarna, 
  	lösta från resorna
  	av himlafurstarnas ängel.

1 800 epochs

	Jag ville veta, vad som väntade
       	de döda har sökt oss
       	i sömn låg vi hemma. 
  	Ammaseus horisont 
  	Ammaseus Horisont
  
  
  
More examples of generated poems, can be found in the textfile: <a href="https://github.com/svenskscifi/karinboye/blob/master/exampleresults.txt">exampleresults.txt</a>
 
 

 
 # Test the trained model
 
You can download the final model here <a href="">PretrainedGPT-2KarinBoye</a> and then test it by running it at this free google colab resource <a href="https://colab.research.google.com/drive/1VLG8e7YSEwypxU-noRNhsv5dW4NfTGce">Run a GPT-2 Text-Generating Model</a>, by using the instructions below (you have to have a google drive account with at least 10 GB of free storage to run this).

1. Copy the trained model above to your google drive.
2. Open the link to the <a href="https://colab.research.google.com/drive/1VLG8e7YSEwypxU-noRNhsv5dW4NfTGce">colab</a> above in a chrome webbrowser
2. Make a local copy of the colab in your google drive: <i>File->Save a copy in drive</i>.
3. Run the 1st and 2nd cells in order to initialize tensorflow and allocated a free GPU resource from google colab.
4. Run the 3rd cell with the 355M model as <code>gpt2.download_gpt2(model_name="355M")</code>
5. Run the 4th cell, mounting your google drive and follow instructions.
6. Jump to the 9th cell <i>Load a Trained model Checkpoint</i> and run it with:
<code>gpt2.copy_checkpoint_from_gdrive(run_name='PretrainedGPT-2KarinBoye')</code> and wait for the model to upload.
7. Run the 10th cell by <code> gpt2.load_gpt2(sess, run_name='PretrainedGPT-2KarinBoye')</code>
8. Run the 11th cell <i>Generate Text From The Trained Model</i>

If you want to generate output with a specific seed and/or control the temperature of the output jump to the next cell <i></i>. Lower temperature will give more consistent but less creative output, whereas higher temeprature will prodouce less coherent but more creative results. For the results in <i>exampleresults.txt</i> a temperature of 0.8 was used.

If you want to generate output into a textfile then jump to the 13th cell <i>Generate Text From The Pretrained Model</i> and follow instructions.

It is also possible to make limited training of the model at this colab, but usually not for more than a couple of hours before the runtime expires.

Make sure to include license information <a href="https://github.com/svenskscifi/karinboye/blob/master/LICENSE.txt">LICENSE.txt</a>  if you use text generated by this model.






