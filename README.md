# About primDB
Current mass spectrometers has ability to produce precursor ion mass with high accuracy and small error tolerance which is used by most of the mass spectrometry softwares (e.g Mascot) to identify protein and peptide from it derived fragmented ions (MS/MS). 

Finding the occurance of precursor ion mass and protein and peptide identification from a large collection of sample is trivial. primDB was built to store the MS/MS spectra information from the mzML (converted from RAW) and peptide information from the pepxML (Mascot output) files into a database. A browser based application fasciliate user to lookup precursor ion and it's protein and peptide identification from whole set of experiments at once.

### Files
* mzML - RAW data generated by the tandem mass spectrometer is converted into the mzML format for better representation and interpretation using msconvert.
* pepXML - Exported from the Mascot search result.



### Installation



1.	  Install Python 2.7.2
	Source : http://www.python.org/getit/releases/2.7.2/
	
2.   pip install - requirements.txt
		
3. #####  Postgresql settings
           psql -d template1 -U postgres
           CREATE USER primdbuser WITH PASSWORD '****';
           CREATE DATABASE primdb;
           GRANT ALL PRIVILEGES ON DATABASE primdb to primdbuser;

4. Create tables on the primdb database

           $ python manage.py validate (check if there are any errors in models 	and applications settings)
           
           $ python manage.py syncdb (create tables from the database models)

5. ####Upload mzML and pepxml file content into database

*  Upload (mzML)into database
 
       
        $ python mzml.py experiment_glucose.mzML
        
          
* Upload (pepXML)into database 
          
        $ python pepxml.py experiment_glucose.xml
