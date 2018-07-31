# Delta-Theta

#include <iostream>
#include <fstream>
#include <cstdlib>
#include <vector>
#include <string>
#include <cmath>
#include <iomanip>

using namespace std;

// Structure.
struct Metrology_Measurement
{
  double coordinates; //id associated with the coordinates from the microscope
};

int main()
{
  vector<Metrology_Measurement>MeasurementInfo(0);

  Metrology_Measurement data; 

  ifstream myFile; 
  myFile.open("Measurements0307.csv"); 

  if(!myFile) 
    {
      cerr << "Error, opening file. ";
      exit(EXIT_FAILURE);
    }

  while(myFile >> data.coordinates)
    {
     
      MeasurementInfo.push_back(data);
    }

  myFile.close();

  // Next display the result
  for(size_t i=0; i< MeasurementInfo.size(); i++)
    {
      // cout << "Coordinates: " <<  MeasurementInfo[i].coordinates << endl;
    }
  cout << setprecision(12);
  /*
    cout << "X-Coordinate 1: " << MeasurementInfo[0].coordinates << endl;
    cout << "Y-Coordinate 1: " << MeasurementInfo[1].coordinates << endl;
    cout << "X-Coordinate 2: " << MeasurementInfo[2].coordinates << endl;
    cout << "Y-Coordinate 2: " << MeasurementInfo[3].coordinates << endl;
    cout << "X-Coordinate 3: " << MeasurementInfo[4].coordinates << endl;
    cout << "Y-Coordinate 3: " << MeasurementInfo[5].coordinates << endl;
    cout << "X-Coordinate 4: " << MeasurementInfo[6].coordinates << endl;
    cout << "Y-Coordinate 4: " << MeasurementInfo[7].coordinates << endl;
    cout << "X-Coordinate 5: " << MeasurementInfo[8].coordinates << endl;
    cout << "Y-Coordinate 5: " << MeasurementInfo[9].coordinates << endl;
    cout << "X-Coordinate 6: " << MeasurementInfo[10].coordinates << endl;
    cout << "Y-Coordinate 6: " << MeasurementInfo[11].coordinates << endl;
    cout << "X-Coordinate 7: " << MeasurementInfo[12].coordinates << endl;
    cout << "Y-Coordinate 7: " << MeasurementInfo[13].coordinates << endl;
    cout << "X-Coordinate 8: " << MeasurementInfo[14].coordinates << endl;
    cout << "Y-Coordinate 8: " << MeasurementInfo[15].coordinates << endl;
    cout << "X-Coordinate 9: " << MeasurementInfo[16].coordinates << endl;
    cout << "Y-Coordinate 9: " << MeasurementInfo[17].coordinates << endl;
  */
  //Transforming each point to the absolute coordinate
  float X1;
  X1 = MeasurementInfo[0].coordinates;

  float Y1;
  Y1 = MeasurementInfo[1].coordinates;
   
  float X2;
  X2 = MeasurementInfo[2].coordinates;

  float Y2;
  Y2 = MeasurementInfo[3].coordinates;

  float X3;
  X3 =  MeasurementInfo[4].coordinates + MeasurementInfo[2].coordinates;

  float Y3;
  Y3 = MeasurementInfo[5].coordinates + MeasurementInfo[3].coordinates;

  float X4;
  X4 = MeasurementInfo[6].coordinates + MeasurementInfo[4].coordinates + MeasurementInfo[2].coordinates;

  float Y4;
  Y4 = MeasurementInfo[7].coordinates+ MeasurementInfo[5].coordinates + MeasurementInfo[3].coordinates;

  float X5;
  X5 = MeasurementInfo[8].coordinates + MeasurementInfo[6].coordinates + MeasurementInfo[4].coordinates + MeasurementInfo[2].coordinates;

  float Y5;
  Y5 = MeasurementInfo[9].coordinates + MeasurementInfo[7].coordinates + MeasurementInfo[5].coordinates + MeasurementInfo[3].coordinates;

  float X6;
  X6 = MeasurementInfo[10].coordinates + MeasurementInfo[8].coordinates + MeasurementInfo[6].coordinates + MeasurementInfo[4].coordinates + MeasurementInfo[2].coordinates;

  float Y6;
  Y6 =  MeasurementInfo[11].coordinates + MeasurementInfo[9].coordinates + MeasurementInfo[7].coordinates + MeasurementInfo[5].coordinates + MeasurementInfo[3].coordinates;

  float X7;
  X7 =  MeasurementInfo[12].coordinates + MeasurementInfo[10].coordinates + MeasurementInfo[8].coordinates + MeasurementInfo[6].coordinates + MeasurementInfo[4].coordinates + MeasurementInfo[2].coordinates;

  float Y7;
  Y7 =  MeasurementInfo[13].coordinates + MeasurementInfo[11].coordinates + MeasurementInfo[9].coordinates + MeasurementInfo[7].coordinates + MeasurementInfo[5].coordinates + MeasurementInfo[3].coordinates;

  float X8;
  X8 = MeasurementInfo[14].coordinates + MeasurementInfo[12].coordinates + MeasurementInfo[10].coordinates + MeasurementInfo[8].coordinates + MeasurementInfo[6].coordinates + MeasurementInfo[4].coordinates + MeasurementInfo[2].coordinates;

  float Y8;
  Y8 = MeasurementInfo[15].coordinates + MeasurementInfo[13].coordinates + MeasurementInfo[11].coordinates + MeasurementInfo[9].coordinates + MeasurementInfo[7].coordinates + MeasurementInfo[5].coordinates + MeasurementInfo[3].coordinates;

  float X9;
  X9 = MeasurementInfo[16].coordinates + MeasurementInfo[14].coordinates + MeasurementInfo[12].coordinates + MeasurementInfo[10].coordinates + MeasurementInfo[8].coordinates + MeasurementInfo[6].coordinates + MeasurementInfo[4].coordinates + MeasurementInfo[2].coordinates;

  float Y9;
  Y9 = MeasurementInfo[17].coordinates + MeasurementInfo[15].coordinates + MeasurementInfo[13].coordinates + MeasurementInfo[11].coordinates + MeasurementInfo[9].coordinates + MeasurementInfo[7].coordinates + MeasurementInfo[5].coordinates + MeasurementInfo[3].coordinates;
   
  /*
    cout << "X-Coordinate 1: " << X1 << endl; //0
    cout << "Y-Coordinate 1: " << Y1 << endl; //0
    cout << "X-Coordinate 2: " << X2 << endl; //-97.751
    cout << "Y-Coordinate 2: " << Y2 << endl; //0.777
    cout << "X-Coordinate 3: " << X3 << endl; //-98.12
    cout << "Y-Coordinate 3: " << Y3 << endl; //-47.523
    cout << "X-Coordinate 4: " << X4 << endl; //-0.379
    cout << "Y-Coordinate 4: " << Y4 << endl; //-48.283
    cout << "X-Coordinate 5: " << X5 << endl; //0
    cout << "Y-Coordinate 5: " << Y5 << endl; //0.019
    cout << "X-Coordinate 6: " << X6 << endl; //-1.243
    cout << "Y-Coordinate 6: " << Y6 << endl; //-0.008
    cout << "X-Coordinate 7: " << X7 << endl; //-96.494
    cout << "Y-Coordinate 7: " << Y7 << endl; //0.81
    cout << "X-Coordinate 8: " << X8 << endl; //-96.889
    cout << "Y-Coordinate 8: " << Y8 << endl; //-47.503
    cout << "X-Coordinate 9: " << X9 << endl; //-1.638
    cout << "Y-Coordinate 9: " << Y9 << endl; //-48.293
  */

  /*
  Horizontal Line for the bottom sensor has points (0,0) to (-97.751,0.777) and (-0.38, -48.283) to (-98.12, -47.523) 
  Legends: 
  bottom sensor upper: M1 (slope), Theta1 (angle)
  bottom sensor lower: M2 (slope), Theta2 (angle)
  */
  cout << "Horizontal Lines for the bottom sensor" << endl;
  double m1HU; //slope bottom sensor upper
  m1HU = Y2/X2;
  cout << "M1: "<< m1HU << endl;

  double thetaHUBottom;
  thetaHUBottom = atan(m1HU);
  cout << "Theta1: " <<  thetaHUBottom << endl;

  double m2HL; //bottom sensor lower
  m2HL = (Y3 - Y4)/(X3 - X4); //bottom sensor 
  cout << "M2: " << m2HL << endl;

  double thetaHLBottom;
  thetaHLBottom = atan(m2HL);
  cout << "Theta2: " <<  thetaHLBottom << endl;

  //Deltatheta
  double DeltaThetaBottom;
  DeltaThetaBottom = abs(thetaHUBottom - thetaHLBottom);
  cout<<"Delta Theta Bottom Sensor: "<< DeltaThetaBottom<< endl;

  /*
  Horizontal Line for the top sensor has points  (-1.243, 0.008) to (-96.494, 0.81) and (-1.638, -48.293) to (-96.889, -47.503)
  Legends: 
  top sensor upper: M3 (slope), Theta3 (angle)
  top sensor slower: M4 (slope), Theta4 (angle)
  */
  cout <<""<<endl;
  cout << "Horizontal Lines for the top sensor" << endl;

  double m2HU; //top sensor 
  m2HU = (Y7 - Y6)/(X7 - X6);
  cout << "M3: " << m2HU << endl;

  double thetaHUTop;
  thetaHUTop = atan(m2HU);
  cout << "Theta3: " <<  thetaHUTop << endl;

  double m1HL;
  m1HL = (Y9 - Y8)/(X9 - X8); //top sensor 
  cout << "M4: "<< m1HL << endl;

  double thetaHLTop;
  thetaHLTop = atan(m1HL);
  cout << "Theta4: " <<  thetaHLTop << endl;

  double DeltaThetaTop;
  DeltaThetaTop = abs(thetaHUTop - thetaHLTop);
  cout<<"Delta Theta Top Sensor: "<< DeltaThetaTop<< endl;

  cout <<""<<endl;
  cout<<"Some other checks" << endl; //The difference between the outer marker from the inner marker is 1.25mm

  double Corner1;
  Corner1 = abs(X6 - X1);
  cout << "Corner 1: " << Corner1 << endl;

  double Corner2;
  Corner2 = abs(X2 - X7);
  cout << "Corner 2: " << Corner2 << endl;

  double Corner3;
  Corner3 = abs(X3 - X8);
  cout << "Corner 3: " << Corner3 << endl;

  double Corner4;
  Corner4 = abs(X9 - X4);
  cout << "Corner 4: " << Corner4 << endl;
  
  
  return 0;
}
