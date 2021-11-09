PyTorch is one of the most powerful and adaptable deep learning frameworks for Python

A good portion of deep learning research is done in PyTorch. The other half in Tensorflow/Keras. 

Despite what you see that deep learning is hard. PyTorch makes it very simple to quickly develop and train models. 

A PyTorch Script is divided into three parts
1. Data Processing and Loading
2. Model Definition
3. Training, Development, and Testing Loop 

1. Data Processing and Loading
Taking raw data and converting it to something pytorch can read is the most important step\
Torch is based on the object of a tensor which is similar to numpy array. \
Only tensors can be fed through the model\
To Process Images, we use the transforms library to prepare our data\
That is why we use transforms.ToTensor() to convert the JPGs to tensors of integers

Other Transformations
We use other transforms to clean up dirty data and standardize it\
Grayscaling simplifies the problem down from 3 Tensors of data (RGB) to 1 tensor of data (Grayscale)\
Normalizing helps reduce noise within the dataset\
There are other transformations like adding more noise or rotating the image or changing some of the color. These data augmenetations are really good for increasing the size of your training data while also helping the model generalize

After we have our data processed, we can move on to splitting and loading.\
Splitting our dataset will allow use to check the progress of the model by hiding a set of data for it to see later. This helps our model generalize and not just memorize the training data.

After splitting, we need to get our data into a dataloader \
A dataloader is a special object that helps batch our pictures together while providing an easy to use iterator when we train\
Batches are a way of speeding up our training while helping to stabilize the model \
It is much simpler to use the pytorch dataloader than doing your own batching and iterating as it saves memory

2. Model Definition
Models in Pytorch are divided Python Classes that have two important sections. 
1. The Layer Definition
2. The Forward Pass

The Layer Definition is where you declare what different types of layers like Convultion layers, Fully Connected Layers, Residual Layers, activtation functions, and pooling/normalizing steps you want. \
The Forward Pass is how is telling the route that your data will take once it goes into the model. It is a roadmap of the different layers that your data will step through. THIS IS A VERY IMPORTANT THING TO GET RIGHT. YOU NEED TO HAVE THE SIZE OF THE OUTPUT OF THE LAST LAYER MATCH THE SIZE OF THE INPUT OF THE NEXT LAYER. 

In addition to these things, you need to define a loss function and an optimizer. \
The Loss function tells the model how wrong you were on the task and gives a numerical value telling how wrong it was. The optimizer takes that loss data and calculates the best way to change the parameters to decrease the loss and become more accurate.

3. Training, Development, and Testing Loop 
After we have declared a model, and loaded our data into a dataloader it is time to use them both. \
A model is trained for a variety of epochs. An epoch is one pass through the entirity of the training set. \
The basic outline for a training loop is
```
for x many epochs:
    for batch, labels in train data_set:
        preds = forwardpass(batch)
        loss = lossfunc(preds)
        loss.backprop()
        optimize()
```
The development and testing loop look alot alike. An importance difference is that torch.no_grad() is included. \
This important as we dont want the model to learn these datasets. 
```
with torch.no_grad()
    for batch, labels in dev/test data_set:
        preds = forwardpass(batch)
```
The main difference between development and test is that the development loop will be at the end of each epoch while testing is at the end of training.

I think thats it in summary 
1. Process Data
2. Split Data
3. Load Data
4. Make Model
5. Make Optimizer and Loss
6. Set up Training/Development/Testing Loop
