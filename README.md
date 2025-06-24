# business-analysis
import React, { useState } from 'react';
import { LineChart, Line, XAxis, YAxis, CartesianGrid, Tooltip, Legend, BarChart, Bar, PieChart, Pie, Cell, ResponsiveContainer, AreaChart, Area, RadarChart, PolarGrid, PolarAngleAxis, PolarRadiusAxis, Radar, ScatterChart, Scatter } from 'recharts';

const CosmeticsAnalysisDashboard = () => {
  const [activeTab, setActiveTab] = useState('market');

  // Market Size Data
  const marketSizeData = [
    { year: '2019', global: 380, skincare: 145, makeup: 65, haircare: 87, fragrance: 52, other: 31 },
    { year: '2020', global: 365, skincare: 140, makeup: 58, haircare: 85, fragrance: 48, other: 34 },
    { year: '2021', global: 395, skincare: 155, makeup: 62, haircare: 89, fragrance: 50, other: 39 },
    { year: '2022', global: 430, skincare: 170, makeup: 68, haircare: 95, fragrance: 55, other: 42 },
    { year: '2023', global: 465, skincare: 185, makeup: 73, haircare: 102, fragrance: 58, other: 47 },
    { year: '2024', global: 495, skincare: 198, makeup: 78, haircare: 108, fragrance: 62, other: 49 },
    { year: '2025', global: 525, skincare: 210, makeup: 82, haircare: 115, fragrance: 65, other: 53 }
  ];

  // Regional Market Data
  const regionalData = [
    { region: 'North America', market_share: 25, growth_rate: 4.2, value: 131 },
    { region: 'Europe', market_share: 22, growth_rate: 3.8, value: 109 },
    { region: 'Asia Pacific', market_share: 35, growth_rate: 6.8, value: 173 },
    { region: 'Latin America', market_share: 8, growth_rate: 5.2, value: 40 },
    { region: 'Middle East & Africa', market_share: 10, growth_rate: 7.1, value: 50 }
  ];

  // Consumer Demographics
  const consumerData = [
    { age_group: '18-24', percentage: 22, spending: 180 },
    { age_group: '25-34', percentage: 28, spending: 320 },
    { age_group: '35-44', percentage: 25, spending: 280 },
    { age_group: '45-54', percentage: 15, spending: 220 },
    { age_group: '55+', percentage: 10, spending: 150 }
  ];

  // Purchase Channels
  const channelData = [
    { name: 'Online', value: 35, growth: 12.5 },
    { name: 'Department Stores', value: 25, growth: 2.1 },
    { name: 'Specialty Stores', value: 20, growth: 4.2 },
    { name: 'Mass Market', value: 15, growth: 1.8 },
    { name: 'Direct Sales', value: 5, growth: 8.3 }
  ];

  // Competitive Analysis Data
  const competitorData = [
    { company: "L'Oréal", market_share: 15.2, revenue: 38.2, growth: 4.8, innovation_score: 9.2 },
    { company: 'Unilever', market_share: 8.1, revenue: 20.3, growth: 3.2, innovation_score: 7.8 },
    { company: 'P&G', market_share: 7.3, revenue: 18.4, growth: 2.9, innovation_score: 8.1 },
    { company: 'Estée Lauder', market_share: 6.8, revenue: 17.1, growth: 5.6, innovation_score: 8.9 },
    { company: 'Shiseido', market_share: 4.2, revenue: 10.5, growth: 1.8, innovation_score: 8.3 },
    { company: 'Coty', market_share: 3.9, revenue: 9.8, growth: -0.5, innovation_score: 6.7 }
  ];

  // Financial Performance Data
  const financialData = [
    { metric: 'Gross Margin', industry_avg: 65, top_performer: 75, your_company: 62 },
    { metric: 'Operating Margin', industry_avg: 12, top_performer: 18, your_company: 10 },
    { metric: 'R&D Investment', industry_avg: 3.2, top_performer: 4.8, your_company: 2.8 },
    { metric: 'Marketing Spend', industry_avg: 25, top_performer: 30, your_company: 22 },
    { metric: 'Inventory Turnover', industry_avg: 4.2, top_performer: 6.1, your_company: 3.8 }
  ];

  // Trend Analysis
  const trendData = [
    { trend: 'Clean Beauty', interest: 85, market_impact: 78, adoption_rate: 65 },
    { trend: 'Personalization', interest: 75, market_impact: 82, adoption_rate: 45 },
    { trend: 'Sustainability', interest: 88, market_impact: 76, adoption_rate: 58 },
    { trend: 'Male Grooming', interest: 72, market_impact: 68, adoption_rate: 52 },
    { trend: 'K-Beauty', interest: 68, market_impact: 71, adoption_rate: 48 },
    { trend: 'Anti-Aging', interest: 80, market_impact: 85, adoption_rate: 72 }
  ];

  const COLORS = ['#8884d8', '#82ca9d', '#ffc658', '#ff7c7c', '#8dd1e1', '#d084d0'];

  const TabButton = ({ tab, label, active, onClick }) => (
    <button
      onClick={onClick}
      className={`px-6 py-3 font-medium rounded-t-lg transition-colors duration-200 ${
        active 
          ? 'bg-blue-600 text-white border-b-2 border-blue-600' 
          : 'bg-gray-100 text-gray-700 hover:bg-gray-200'
      }`}
    >
      {label}
    </button>
  );

  const MetricCard = ({ title, value, change, color = "blue" }) => (
    <div className="bg-white p-6 rounded-lg shadow-md border-l-4 border-blue-500">
      <h3 className="text-lg font-semibold text-gray-800 mb-2">{title}</h3>
      <div className="flex items-center justify-between">
        <span className="text-3xl font-bold text-gray-900">{value}</span>
        <span className={`text-sm font-medium ${change >= 0 ? 'text-green-600' : 'text-red-600'}`}>
          {change >= 0 ? '↗' : '↘'} {Math.abs(change)}%
        </span>
      </div>
    </div>
  );

  return (
    <div className="min-h-screen bg-gray-50 p-6">
      <div className="max-w-7xl mx-auto">
        <h1 className="text-4xl font-bold text-center mb-8 text-gray-800">
          Cosmetics Business Analysis Dashboard
        </h1>
        
        {/* Navigation Tabs */}
        <div className="flex flex-wrap justify-center mb-8 border-b">
          <TabButton 
            tab="market" 
            label="Market Analysis" 
            active={activeTab === 'market'} 
            onClick={() => setActiveTab('market')} 
          />
          <TabButton 
            tab="consumer" 
            label="Consumer Insights" 
            active={activeTab === 'consumer'} 
            onClick={() => setActiveTab('consumer')} 
          />
          <TabButton 
            tab="competition" 
            label="Competitive Analysis" 
            active={activeTab === 'competition'} 
            onClick={() => setActiveTab('competition')} 
          />
          <TabButton 
            tab="financial" 
            label="Financial Performance" 
            active={activeTab === 'financial'} 
            onClick={() => setActiveTab('financial')} 
          />
          <TabButton 
            tab="trends" 
            label="Market Trends" 
            active={activeTab === 'trends'} 
            onClick={() => setActiveTab('trends')} 
          />
        </div>

        {/* Market Analysis Tab */}
        {activeTab === 'market' && (
          <div className="space-y-8">
            <div className="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
              <MetricCard title="Market Size" value="$495B" change={6.5} />
              <MetricCard title="Growth Rate" value="6.2%" change={0.8} />
              <MetricCard title="Key Segments" value="5" change={0} />
              <MetricCard title="Market Leaders" value="15%" change={2.1} />
            </div>

            <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
              <div className="bg-white p-6 rounded-lg shadow-md">
                <h3 className="text-xl font-semibold mb-4">Global Market Size by Segment</h3>
                <ResponsiveContainer width="100%" height={300}>
                  <AreaChart data={marketSizeData}>
                    <CartesianGrid strokeDasharray="3 3" />
                    <XAxis dataKey="year" />
                    <YAxis />
                    <Tooltip formatter={(value) => [`$${value}B`, '']} />
                    <Legend />
                    <Area type="monotone" dataKey="skincare" stackId="1" stroke="#8884d8" fill="#8884d8" />
                    <Area type="monotone" dataKey="makeup" stackId="1" stroke="#82ca9d" fill="#82ca9d" />
                    <Area type="monotone" dataKey="haircare" stackId="1" stroke="#ffc658" fill="#ffc658" />
                    <Area type="monotone" dataKey="fragrance" stackId="1" stroke="#ff7c7c" fill="#ff7c7c" />
                    <Area type="monotone" dataKey="other" stackId="1" stroke="#8dd1e1" fill="#8dd1e1" />
                  </AreaChart>
                </ResponsiveContainer>
              </div>

              <div className="bg-white p-6 rounded-lg shadow-md">
                <h3 className="text-xl font-semibold mb-4">Regional Market Share</h3>
                <ResponsiveContainer width="100%" height={300}>
                  <PieChart>
                    <Pie
                      data={regionalData}
                      cx="50%"
                      cy="50%"
                      labelLine={false}
                      label={({ region, market_share }) => `${region}: ${market_share}%`}
                      outerRadius={80}
                      fill="#8884d8"
                      dataKey="market_share"
                    >
                      {regionalData.map((entry, index) => (
                        <Cell key={`cell-${index}`} fill={COLORS[index % COLORS.length]} />
                      ))}
                    </Pie>
                    <Tooltip />
                  </PieChart>
                </ResponsiveContainer>
              </div>
            </div>

            <div className="bg-white p-6 rounded-lg shadow-md">
              <h3 className="text-xl font-semibold mb-4">Regional Growth vs Market Value</h3>
              <ResponsiveContainer width="100%" height={400}>
                <ScatterChart data={regionalData}>
                  <CartesianGrid />
                  <XAxis dataKey="growth_rate" name="Growth Rate" unit="%" />
                  <YAxis dataKey="value" name="Market Value" unit="B" />
                  <Tooltip cursor={{ strokeDasharray: '3 3' }} />
                  <Scatter name="Regions" data={regionalData} fill="#8884d8" />
                </ScatterChart>
              </ResponsiveContainer>
            </div>
          </div>
        )}

        {/* Consumer Insights Tab */}
        {activeTab === 'consumer' && (
          <div className="space-y-8">
            <div className="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
              <MetricCard title="Avg Spending" value="$230" change={5.2} />
              <MetricCard title="Online Growth" value="12.5%" change={3.1} />
              <MetricCard title="Brand Loyalty" value="68%" change={-2.3} />
              <MetricCard title="Mobile Users" value="72%" change={8.4} />
            </div>

            <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
              <div className="bg-white p-6 rounded-lg shadow-md">
                <h3 className="text-xl font-semibold mb-4">Consumer Demographics by Age</h3>
                <ResponsiveContainer width="100%" height={300}>
                  <BarChart data={consumerData}>
                    <CartesianGrid strokeDasharray="3 3" />
                    <XAxis dataKey="age_group" />
                    <YAxis yAxisId="left" />
                    <YAxis yAxisId="right" orientation="right" />
                    <Tooltip />
                    <Legend />
                    <Bar yAxisId="left" dataKey="percentage" fill="#8884d8" name="Market Share %" />
                    <Bar yAxisId="right" dataKey="spending" fill="#82ca9d" name="Avg Spending $" />
                  </BarChart>
                </ResponsiveContainer>
              </div>

              <div className="bg-white p-6 rounded-lg shadow-md">
                <h3 className="text-xl font-semibold mb-4">Purchase Channels Distribution</h3>
                <ResponsiveContainer width="100%" height={300}>
                  <PieChart>
                    <Pie
                      data={channelData}
                      cx="50%"
                      cy="50%"
                      labelLine={false}
                      label={({ name, value }) => `${name}: ${value}%`}
                      outerRadius={80}
                      fill="#8884d8"
                      dataKey="value"
                    >
                      {channelData.map((entry, index) => (
                        <Cell key={`cell-${index}`} fill={COLORS[index % COLORS.length]} />
                      ))}
                    </Pie>
                    <Tooltip />
                  </PieChart>
                </ResponsiveContainer>
              </div>
            </div>

            <div className="bg-white p-6 rounded-lg shadow-md">
              <h3 className="text-xl font-semibold mb-4">Channel Growth Comparison</h3>
              <ResponsiveContainer width="100%" height={300}>
                <BarChart data={channelData}>
                  <CartesianGrid strokeDasharray="3 3" />
                  <XAxis dataKey="name" />
                  <YAxis />
                  <Tooltip />
                  <Legend />
                  <Bar dataKey="growth" fill="#ffc658" name="Growth Rate %" />
                </BarChart>
              </ResponsiveContainer>
            </div>
          </div>
        )}

        {/* Competitive Analysis Tab */}
        {activeTab === 'competition' && (
          <div className="space-y-8">
            <div className="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
              <MetricCard title="Market Leader" value="15.2%" change={0.8} />
              <MetricCard title="Top 6 Share" value="45.5%" change={1.2} />
              <MetricCard title="New Entrants" value="23" change={15.0} />
              <MetricCard title="Avg Innovation" value="8.2" change={4.1} />
            </div>

            <div className="bg-white p-6 rounded-lg shadow-md">
              <h3 className="text-xl font-semibold mb-4">Market Share vs Revenue</h3>
              <ResponsiveContainer width="100%" height={400}>
                <BarChart data={competitorData}>
                  <CartesianGrid strokeDasharray="3 3" />
                  <XAxis dataKey="company" />
                  <YAxis yAxisId="left" />
                  <YAxis yAxisId="right" orientation="right" />
                  <Tooltip />
                  <Legend />
                  <Bar yAxisId="left" dataKey="market_share" fill="#8884d8" name="Market Share %" />
                  <Bar yAxisId="right" dataKey="revenue" fill="#82ca9d" name="Revenue $B" />
                </BarChart>
              </ResponsiveContainer>
            </div>

            <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
              <div className="bg-white p-6 rounded-lg shadow-md">
                <h3 className="text-xl font-semibold mb-4">Growth Rate Comparison</h3>
                <ResponsiveContainer width="100%" height={300}>
                  <BarChart data={competitorData}>
                    <CartesianGrid strokeDasharray="3 3" />
                    <XAxis dataKey="company" />
                    <YAxis />
                    <Tooltip />
                    <Bar dataKey="growth" fill="#ffc658" name="Growth Rate %" />
                  </BarChart>
                </ResponsiveContainer>
              </div>

              <div className="bg-white p-6 rounded-lg shadow-md">
                <h3 className="text-xl font-semibold mb-4">Innovation Score vs Market Share</h3>
                <ResponsiveContainer width="100%" height={300}>
                  <ScatterChart data={competitorData}>
                    <CartesianGrid />
                    <XAxis dataKey="innovation_score" name="Innovation Score" />
                    <YAxis dataKey="market_share" name="Market Share" unit="%" />
                    <Tooltip cursor={{ strokeDasharray: '3 3' }} />
                    <Scatter name="Companies" data={competitorData} fill="#8884d8" />
                  </ScatterChart>
                </ResponsiveContainer>
              </div>
            </div>
          </div>
        )}

        {/* Financial Performance Tab */}
        {activeTab === 'financial' && (
          <div className="space-y-8">
            <div className="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
              <MetricCard title="Industry Avg Margin" value="65%" change={2.1} />
              <MetricCard title="R&D Investment" value="3.2%" change={0.5} />
              <MetricCard title="Marketing Spend" value="25%" change={1.8} />
              <MetricCard title="Inventory Turnover" value="4.2x" change={-0.3} />
            </div>

            <div className="bg-white p-6 rounded-lg shadow-md">
              <h3 className="text-xl font-semibold mb-4">Financial Performance Benchmarking</h3>
              <ResponsiveContainer width="100%" height={400}>
                <BarChart data={financialData}>
                  <CartesianGrid strokeDasharray="3 3" />
                  <XAxis dataKey="metric" />
                  <YAxis />
                  <Tooltip />
                  <Legend />
                  <Bar dataKey="industry_avg" fill="#8884d8" name="Industry Average" />
                  <Bar dataKey="top_performer" fill="#82ca9d" name="Top Performer" />
                  <Bar dataKey="your_company" fill="#ffc658" name="Your Company" />
                </BarChart>
              </ResponsiveContainer>
            </div>

            <div className="bg-white p-6 rounded-lg shadow-md">
              <h3 className="text-xl font-semibold mb-4">Performance Gap Analysis</h3>
              <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                {financialData.map((item, index) => (
                  <div key={index} className="border rounded-lg p-4">
                    <h4 className="font-semibold text-gray-800 mb-2">{item.metric}</h4>
                    <div className="space-y-2">
                      <div className="flex justify-between">
                        <span className="text-sm text-gray-600">Industry Avg:</span>
                        <span className="font-medium">{item.industry_avg}{item.metric.includes('Margin') || item.metric.includes('Investment') || item.metric.includes('Spend') ? '%' : item.metric.includes('Turnover') ? 'x' : ''}</span>
                      </div>
                      <div className="flex justify-between">
                        <span className="text-sm text-gray-600">Top Performer:</span>
                        <span className="font-medium text-green-600">{item.top_performer}{item.metric.includes('Margin') || item.metric.includes('Investment') || item.metric.includes('Spend') ? '%' : item.metric.includes('Turnover') ? 'x' : ''}</span>
                      </div>
                      <div className="flex justify-between">
                        <span className="text-sm text-gray-600">Your Company:</span>
                        <span className={`font-medium ${item.your_company < item.industry_avg ? 'text-red-600' : 'text-blue-600'}`}>
                          {item.your_company}{item.metric.includes('Margin') || item.metric.includes('Investment') || item.metric.includes('Spend') ? '%' : item.metric.includes('Turnover') ? 'x' : ''}
                        </span>
                      </div>
                      <div className="text-xs text-gray-500">
                        Gap: {item.your_company < item.industry_avg ? '-' : '+'}{Math.abs(item.your_company - item.industry_avg).toFixed(1)}
                      </div>
                    </div>
                  </div>
                ))}
              </div>
            </div>
          </div>
        )}

        {/* Market Trends Tab */}
        {activeTab === 'trends' && (
          <div className="space-y-8">
            <div className="grid grid-cols-1 md:grid-cols-4 gap-6 mb-8">
              <MetricCard title="Clean Beauty Growth" value="85%" change={12.3} />
              <MetricCard title="Personalization" value="75%" change={18.7} />
              <MetricCard title="Sustainability" value="88%" change={9.8} />
              <MetricCard title="Male Grooming" value="72%" change={22.1} />
            </div>

            <div className="bg-white p-6 rounded-lg shadow-md">
              <h3 className="text-xl font-semibold mb-4">Market Trends Analysis</h3>
              <ResponsiveContainer width="100%" height={400}>
                <RadarChart data={trendData}>
                  <PolarGrid />
                  <PolarAngleAxis dataKey="trend" />
                  <PolarRadiusAxis angle={90} domain={[0, 100]} />
                  <Radar name="Consumer Interest" dataKey="interest" stroke="#8884d8" fill="#8884d8" fillOpacity={0.3} />
                  <Radar name="Market Impact" dataKey="market_impact" stroke="#82ca9d" fill="#82ca9d" fillOpacity={0.3} />
                  <Radar name="Adoption Rate" dataKey="adoption_rate" stroke="#ffc658" fill="#ffc658" fillOpacity={0.3} />
                  <Legend />
                  <Tooltip />
                </RadarChart>
              </ResponsiveContainer>
            </div>

            <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
              <div className="bg-white p-6 rounded-lg shadow-md">
                <h3 className="text-xl font-semibold mb-4">Trend Interest vs Market Impact</h3>
                <ResponsiveContainer width="100%" height={300}>
                  <ScatterChart data={trendData}>
                    <CartesianGrid />
                    <XAxis dataKey="interest" name="Consumer Interest" unit="%" />
                    <YAxis dataKey="market_impact" name="Market Impact" unit="%" />
                    <Tooltip cursor={{ strokeDasharray: '3 3' }} />
                    <Scatter name="Trends" data={trendData} fill="#8884d8" />
                  </ScatterChart>
                </ResponsiveContainer>
              </div>

              <div className="bg-white p-6 rounded-lg shadow-md">
                <h3 className="text-xl font-semibold mb-4">Adoption Rate by Trend</h3>
                <ResponsiveContainer width="100%" height={300}>
                  <BarChart data={trendData}>
                    <CartesianGrid strokeDasharray="3 3" />
                    <XAxis dataKey="trend" />
                    <YAxis />
                    <Tooltip />
                    <Bar dataKey="adoption_rate" fill="#82ca9d" name="Adoption Rate %" />
                  </BarChart>
                </ResponsiveContainer>
              </div>
            </div>
          </div>
        )}
      </div>
    </div>
  );
};

export default CosmeticsAnalysisDashboard;
