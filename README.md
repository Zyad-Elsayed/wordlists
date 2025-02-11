# Wordlists 
## Ghost-CMS-wordlist
a word list for Ghost blogging platform 
## daloradius wordlist
used for managing hotspots and general-purpose ISP deployments.


---
## To generate a directory wordlist from a GitHub repository and then mutate it for enhanced enumeration, you can follow these steps:

1. **Clone the Repository**:
   - Use Git to clone the target repository to your local machine:
     ```bash
     git clone https://github.com/username/repository.git
     cd repository  
     ```

2. **Extract Directory Names**:
   - Use the `find` command to list all directories and subdirectories:
     ```bash
     find . -type d > directories.txt
     ```
   - This command will create a file named `directories.txt` containing all directory paths.

3. **Clean and Format the List**:
   - Remove the leading `./` and any trailing slashes:
     ```bash
     sed -i 's|^\./||; s|/$||' directories.txt
     ```
   - This will format the directory names appropriately for further processing.
   - Extract Unique Directory Names
    ```bash
    awk -F'/' '{for(i=2;i<=NF;i++) print $i}' directories.txt | sort -u > unique_directories.txt
    ```
4. **Mutate the Wordlist**:
   - To enhance the wordlist, you can use tools like `repolist` or `dirlister` to generate additional variations:
     - **RepoList**: A tool that generates wordlists from GitHub repositories.
       - Install RepoList:
         ```bash
         pip3 install repolist
         ```
       - Generate a wordlist:
         ```bash
         repolist -u https://github.com/username/repository -o wordlist.txt
         ```
       - [RepoList GitHub Repository](https://github.com/Ademking/repolist)
     - **DirLister**: A tool that creates wordlists from source code files and directories.
       - Clone and navigate to DirLister:
         ```bash
         git clone https://github.com/jimmy-ly00/dirlister.git
         cd dirlister
         ```
       - Install dependencies and run:
         ```bash
         pip install -r requirements.txt
         python dirlister.py -d /path/to/repository -o wordlist.txt
         ```
       - [DirLister GitHub Repository](https://github.com/jimmy-ly00/dirlister)

