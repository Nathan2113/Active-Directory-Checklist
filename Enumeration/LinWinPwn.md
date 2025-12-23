https://github.com/lefayjey/linWinPwn
  
sudo cp <path/to/linwinpwn> /usr/local/bin/linwinpwn
- alias so you can use it from anywhere
  
when unauthenticated, can run LinWinPwn with the following command unauthenticated
![[../assets/LinWinPwn/image 228.png|image 228.png]]
- ./linWinPwn.sh -t <target> -o <output_path> —auto
  
with creds, it’s very similar
![[../assets/LinWinPwn/image 1 165.png|image 1 165.png]]
- ./linWinPwn.sh -t <target> -u <user> -p <pass> -o <output_path> —auto
  
  
run without auto to use interactive mode
![[../assets/LinWinPwn/image 2 145.png|image 2 145.png]]
![[../assets/LinWinPwn/image 3 129.png|image 3 129.png]]