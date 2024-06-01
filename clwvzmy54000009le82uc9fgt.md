---
title: "How to Upload Images, Videos, and Files to AWS S3 Bucket and Update MongoDB using Node: A Step-by-Step Guide"
seoTitle: "How to Upload Images, Videos, and Files to AWS S3 Bucket using MERN"
seoDescription: "Discover a comprehensive guide on uploading images, videos, and files to AWS S3 Bucket seamlessly integrated with MongoDB using Node.js in a MERN stack."
datePublished: Sat Jun 01 2024 10:46:29 GMT+0000 (Coordinated Universal Time)
cuid: clwvzmy54000009le82uc9fgt
slug: how-to-upload-images-videos-and-files-to-aws-s3-bucket-and-update-mongodb-using-node-a-step-by-step-guide
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/oNPfZozvh-w/upload/19d1682d3ed22c48059c2fabe33cc5ca.jpeg
tags: aws, mern, aws-s3

---

## To create an Aws account, you must sign up using your credit or debit card.

* Select Service and Choose IAM from the menu
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717224309738/f88cc349-d187-46fa-b7c9-3a87f7746a0c.png align="center")
    
    Inside IAM you will see a button for Create user click there and Create a new user and give any name that matches AWS policy **eg: Shiv**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717224459786/001f5e3e-3e54-4a20-adc0-0bf080513769.png align="center")
    
    * Select I want to create an IAM user option and click Next button
        
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717224658596/090ec356-e123-4d92-af05-f08251108f89.png align="center")
    
* You will see three options: '**Add user to group**,' '**Copy permissions**,' and '**Attach policies directly**.' Suppose you are working on a large project that requires multiple policies. In that case, I recommend first creating a new user group in the IAM and attaching the necessary policies to that group. Then, add the user you are creating to this group. Otherwise, you can attach policies directly if only two policies, **AmazonS3FullAccess and IAMUserFullAccess**, are needed.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717225142924/d233563c-0f26-4579-8c58-efb14efc1bce.png align="center")
    
    The final step is to click on Create user.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717225350338/6f53882c-19b0-4579-8f5f-166b0347aae0.png align="center")
    
    ## Similarly, Return to the Services tab on top and Create a new S3Bucket.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717225465009/291e2ca1-2dfd-4db5-a3a6-73a2d72acf18.png align="center")
    
    Simply click on Create Bucket
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717225966619/080bba41-adc1-4f78-9289-d52cac5118cb.png align="center")
    
    And just give a name for eg: **shiv-private-bucket**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717226086895/5b410494-69f7-4421-b1fe-3bdbed5b226e.png align="center")
    
    Leave everything as it is; no need to make any changes. Also, check if 'Block all public access' is enabled. If it is not, click on it to enable it. By default, it should be on. This is to prevent giving any unwanted access to public users.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717226181076/be1d222a-7730-4e06-b542-7f254851e59a.png align="center")
    
    And Here we go Click on Create Bucket at the end of the page.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717226221577/0685842c-2185-40c9-bbc1-1627a1bd0882.png align="center")
    
    Once you create it you should see a bucket name on the **Bucket page** click on that bucket and open it.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717226309572/35fa0ca7-d064-4667-ae96-044168e82e99.png align="center")
    
    Edit Bucket Policy
    
* Now comes the most important part, where you need to make changes to the permissions and the CORS configuration. This is necessary to give the user you created earlier access and to ensure that you can push images, files, or videos from only designated URLs, keeping them secure from hackers.
    
* Go to Permission scroll down to
    
    a. In Bucket policy click on Edit
    
    b. Click on Add new Statement
    
    c. Edit some policies as shown in the pictures below
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717226478031/dad6beb7-3b6f-4c96-9518-a01a1b513dc7.png align="center")
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717226887442/def0632a-b398-4b2e-930c-a0830ec59621.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717226908143/84e98ec6-f40e-4443-9b98-040214dd90a0.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717227296813/6f2393f9-f124-44c2-bdee-1a4001fa8ea8.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717227305089/753af2fa-1bc4-40c6-95aa-600ec1762b32.png align="center")
    
    Save the policy and don't forget to add /\* at the end of the resource bucket so the final policy should look like this
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717227441234/3b0ea108-3951-4201-9530-ce2460705619.png align="center")
    
    **Now let's move to Edit cross-origin resource sharing (CORS)**
    
* Scroll down and see Cross-origin Resource sharing (cors) in the same page inside permission inside bucket as shown in the picture below and click on edit.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717236714192/806cd970-5fdd-430c-aa3a-758fd454aaac.png align="center")
    
    Your Cors configuration should look like this and save it.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717236918382/8b77cc28-8ad8-4d19-a543-2fddbdde42c1.png align="center")
    
    Now go back to User inside Iam go to Security Credentials and generate Access Keys which we will use to programmatic calls to AWS from CLI and follow the image below once you do the process it will generate your **Access Key** and **Password** copy that its sensitive data don't share it anywhere public.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717237104201/40094051-c6c0-4b71-b4ab-3ea099bc31fe.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717237311383/5b24b863-216c-4298-b5b3-b3ca3cd96af7.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717237315968/2b376551-9513-4a63-88a0-5c3c61efa470.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717237318945/b9738267-7180-4209-9dc5-b4a505706279.png align="center")
    
    We are Done with properly creating the S3 bucket.
    

# Now Let's get ready to get hands dirty using code.

I will use JavaScript to create a User schema, and UserModal files.

Let's first Choose how our schema should look like.

```javascript
import mongoose from "mongoose";

const User = new mongoose.Schema({
    fullName: {
        type: String,
        required: [true, 'Full name is required'],
        maxLength: [50, 'Full name cannot exceed 50 characters']
    },
    email: {
        type: String,
        unique: true,
        index: 1,
        required: [true, 'Email is required'],
        maxLength: [50, 'Email cannot exceed 50 characters']
    },
    password: {
        type: String,
        required: [true, 'Password is required']
    },
    images: [
        { type: String }
    ],
    imageUrl: {
        type: String,
        default: null
    }
}, {
    timestamps: true
});

export default mongoose.model("User", UserSchema);
```

And this is the User modal that will help update the mongo database.

```javascript
//Read only one user this is to find admin 
export const getAdminUser = (filter) => {
    return AdminUserSchema.findOne(filter)
}
//<---------------  Update  ----------->
export const updateOneAdminUser = (filter, update) => {
    return AdminUserSchema.findOneAndUpdate(filter, { $set: update }, { new: true });
}
```

Now let's create a separate file named s3Bucket which will hold several function to call the bucket that we created before that you need to install

* @aws-sdk/s3-request-presigner
    
* @aws-sdk/client-s3
    

```javascript
import { S3Client, GetObjectCommand, PutObjectCommand, DeleteObjectCommand } from '@aws-sdk/client-s3';
import { getSignedUrl } from '@aws-sdk/s3-request-presigner';
import dotenv from 'dotenv';

dotenv.config();

const s3Client = new S3Client({
    region: process.env.AWS_REGION,
    credentials: {
        accessKeyId: process.env.AWS_ACCESS_KEY_ID,
        secretAccessKey: process.env.AWS_SECRET_ACCESS_KEY,
    }
});

export const getObjectUrl = async (filename, folderPath) => {
    const command = new GetObjectCommand({
        Bucket: process.env.AWS_S3_BUCKET_NAME,
        Key: `${folderPath}/${filename}`,
    });
    const url = await getSignedUrl(s3Client, command);
    return url;
};

export const putObjectUrl = async (filename, contentType, folderPath) => {
    const command = new PutObjectCommand({
        Bucket: process.env.AWS_S3_BUCKET_NAME,
        Key: `${folderPath}/${filename}`,
        ContentType: contentType,
    });
    const url = await getSignedUrl(s3Client, command, { expiresIn: 3600 });
    return url;
};

export const deleteObjectUrl = async (filename, folderPath) => {
    const command = new DeleteObjectCommand({
        Bucket: process.env.AWS_S3_BUCKET_NAME,
        Key: `${folderPath}/${filename}`,
    })
    await s3Client.send(command);
}
```

Now, create an endpoint in the server file or router. I have created a separate file for the router to follow the clean code principle.

* Defines a route handler for `GET /profileUpload`.
    
* Retrieves `filename`, `filetype` and `_id` from the request query
    
* Specifies `folderPath` as 'profilepic'.
    
* Returns a 400 error if `filename` or `filetype` is missing.
    
* Fetches the admin record using `_id`; returns a 400 error if not found.
    
* Deletes the existing profile image if it exists.
    
* Generates a new image path using the current timestamp and `filename`.
    
* Uploads the new image and gets its URL.
    
* Updates the admin record with the new image path and URL.
    
* Responds with a success message and the upload URL if the update is successful, or a 500 error if it fails.
    

```javascript
router.get('/profileUpload', async (req, res, next) => {
    try {
        const { filename, filetype,_id } = req.query;
        const folderPath = 'profilepic';
        if (!filename || !filetype) {
            return res.status(400).json({
                status: 'error',
                message: 'Filename and filetype are required'
            })
        }
        const existingRecord = await getAdminUser({ _id });
        if (!existingRecord) {
            return res.status(400).json({
                status: "error",
                message: 'Record not found'
            });
        }

        if (existingRecord?.images?.[0]) {
            const oldImagePath = existingRecord?.images?.[0] || null
            await deleteObjectUrl(oldImagePath, folderPath);
        }

        const newImagePath = Date.now() + '-' + filename;
        const uploadUrl = await putObjectUrl(newImagePath, filetype, folderPath);
        const imageUrl = await getObjectUrl(newImagePath, folderPath);

        const response = await updateOneAdminUser({ _id }, {
            images: newImagePath,
            imageUrl: imageUrl
        });
        if (response?._id) {
            res.status(200).json({
                status: 'success',
                message: 'image updated',
                uploadUrl
            });
        } else {
            res.status(500).json({
                status: 'error',
                message: 'please try again'
            });
        }

    } catch (error) {
        next(error)
    }
})
```

Now Once you have successfully created an upload function simply pass the following method then it will pass the image to the s3 bucket

```javascript
// Assuming txQuestionEp is your server endpoint URL
const txQuestionEp = "http://localhost:8000"; // Replace with your actual server URL

const getUploadUrlForProfilePic = async (file, _id) => {
    const option = {
        method: 'get',
        url: `${txQuestionEp}/profileUpload?filename=${encodeURIComponent(file.name)}&filetype=${encodeURIComponent(file.type)}&_id=${_id}`,
        isPrivate: true,
    }
    const response = await apiProcessor(option)
    const { status, message, uploadUrl } = response;
    return { status, message, uploadUrl };
}


const uploadFileToS3 = async (file, _id) => {
    try {
        const { status, message, uploadUrl } = await getUploadUrlForProfilePic(file, _id);
        await axios.put(uploadUrl, file, {
            headers: {
                'Content-Type': file.type,
            },
        });
        return { status, message };
    } catch (error) {
        console.error(error);
    }
};

//This is where you have to pass the image 
const handelOnSave = (e) => {
        e.preventDefault();
        for (const image of images) {
            uploadFileToS3(image);
        }
    };
```