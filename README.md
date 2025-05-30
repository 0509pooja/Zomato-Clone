#Connect master and slave in jenkins
Jenkins can SSH using a .pem key instead of a generated SSH key.

Step-by-step:
Go to Jenkins master
(You said mumbai.pem is already present there.)

Test manual SSH from Jenkins machine:

#sudo -u jenkins ssh -i /home/ubuntu/mumbai.pem ubuntu@3.110.42.241
If that gives an error like "Permission denied", then Jenkins doesn't have access to mumbai.pem.

Fix file permission and access:

#sudo mkdir -p /var/lib/jenkins/.ssh
#sudo cp /home/ubuntu/mumbai.pem /var/lib/jenkins/.ssh/mumbai.pem
#sudo chown -R jenkins:jenkins /var/lib/jenkins/.ssh
#sudo chmod 400 /var/lib/jenkins/.ssh/mumbai.pem
Test again as Jenkins user:

#sudo -u jenkins ssh -i /var/lib/jenkins/.ssh/mumbai.pem ubuntu@3.110.42.241
✅ If this connects: you're good to add this key in Jenkins.

✅ Option 2: Manually add Jenkins public key to slave
If you want to use ssh-copy-id or Jenkins's own key, follow these:

Step-by-step:
On Jenkins master, view the public key:

#sudo cat /var/lib/jenkins/.ssh/id_ed25519.pub
Copy that key.

SSH into the slave manually using your .pem (from master or local):
#ssh -i mumbai.pem ubuntu@3.110.42.241
On the slave:
#mkdir -p ~/.ssh
#nano ~/.ssh/authorized_keys
#Set permissions:
#chmod 700 ~/.ssh
#chmod 600 ~/.ssh/authorized_keys
#sudo -u jenkins ssh ubuntu@3.110.42.241
✅ If it works — Jenkins can connect via SSH key.









# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

The page will reload when you make changes.\
You may also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can't go back!**

If you aren't satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you're on your own.

You don't have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn't feel obligated to use this feature. However we understand that this tool wouldn't be useful if you couldn't customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)
# Zomato-Clone
