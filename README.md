# testing

pipeline{

    // agent {
    //     node {
    //         label 'master'
    //     }
    // }


    agent any



    stages {

        stage('Check out source code')
        {
            steps{
                sh """
                    rm -rf test-repo 
                    git clone git@github.com:tasib-parabellum/test-repo.git
                """
            }
        }



        stage('Build code 1')
        {
            steps{
                
                // we can create a compare folder where we will be storing 
                // our comparison files for all the repos and its sub-folders/files.

                sh """
                    
                    cd test-repo/
                    
                    find dir1/ -type f -exec md5sum {} + | sort -k 2 > ../dir1.txt
                    
                    cd ..
                    
                    cat dir1.txt
                    
                    ls -lah
                    
                    cd code-bkp/

                    find dir1/ -type f -exec md5sum {} + | sort -k 2 > ../dir2.txt
                    
                    cd ..
                    
                    cat dir2.txt
                    
                    ls -lah

                    if cmp -s "dir1.txt" "dir2.txt"; then
                        printf 'The file is the same\n'
                    else
                        printf 'The file is different\n'
                    fi

				"""
                    
				}
			}



        stage('Build code 2')
        {
            steps{
                
                // we can create a compare folder where we will be storing 
                // our comparison files for all the repos and its sub-folders/files.

                sh """
                    
                    cd test-repo/
                    
                    find dir2/ -type f -exec md5sum {} + | sort -k 2 > ../dir1.txt
                    
                    cd ..
                    
                    cat dir1.txt
                    
                    ls -lah
                    
                    cd code-bkp/

                    find dir2/ -type f -exec md5sum {} + | sort -k 2 > ../dir2.txt
                    
                    cd ..
                    
                    cat dir2.txt
                    
                    ls -lah

                    if cmp -s "dir1.txt" "dir2.txt"; then
                        printf 'The file is the same\n'
                    else
                        printf 'The file is different\n'
                    fi

				"""
                    
				}
			}



        stage('Build code 3')
        {
            steps{
                
                // we can create a compare folder where we will be storing 
                // our comparison files for all the repos and its sub-folders/files.

                sh """
                    
                    cd test-repo/
                    
                    find dir3/ -type f -exec md5sum {} + | sort -k 2 > ../dir1.txt
                    
                    cd ..
                    
                    cat dir1.txt
                    
                    ls -lah
                    
                    cd code-bkp/

                    find dir3/ -type f -exec md5sum {} + | sort -k 2 > ../dir2.txt
                    
                    cd ..
                    
                    cat dir2.txt
                    
                    ls -lah

                    if cmp -s "dir1.txt" "dir2.txt"; then
                        printf 'The file is the same\n'
                    else
                        printf 'The file is different\n'
                    fi

				"""
                    
				}
			}



        stage('Build code 4')
        {
            steps{
                
                // we can create a compare folder where we will be storing 
                // our comparison files for all the repos and its sub-folders/files.

                sh """
                    
                    cd test-repo/
                    
                    find dir4/ -type f -exec md5sum {} + | sort -k 2 > ../dir1.txt
                    
                    cd ..
                    
                    cat dir1.txt
                    
                    ls -lah
                    
                    cd code-bkp/

                    find dir4/ -type f -exec md5sum {} + | sort -k 2 > ../dir2.txt
                    
                    cd ..
                    
                    cat dir2.txt
                    
                    ls -lah

                    if cmp -s "dir1.txt" "dir2.txt"; then
                        printf 'The file is the same\n'
                    else
                        printf 'The file is different\n'
                    fi

				"""
                    
				}
			}


        stage('remove and update code folder')
        {
            steps{
                
                sh """
                    
                    rm -rf  code-bkp

                    ls -lah

                    cp -rf test-repo code-bkp

                    ls -lah
                    
				"""
                    
				}
			}

	}
}
