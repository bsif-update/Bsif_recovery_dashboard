// React component for Erman Cikan's Interactive Forensic Asset Tracing Dashboard
import React from 'react';
import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Share2 } from 'lucide-react';
import { BarChart, Bar, XAxis, YAxis, Tooltip, ResponsiveContainer } from 'recharts';

const txData = [
  { date: 'Jun 1', amount: 50000 },
  { date: 'Jun 5', amount: 25000 },
  { date: 'Jun 15', amount: 40000 },
  { date: 'Jun 20', amount: 85000 },
];

export default function ForensicDashboard() {
  const shareLink = "https://t.me/Web3RecoveryIntel";
  const downloadReport = () => {
    // Placeholder for future PDF download integration
    alert("PDF report download is coming soon.");
  };

  return (
    <div className="p-6 max-w-6xl mx-auto bg-white rounded-2xl shadow-md">
      <h1 className="text-3xl font-bold text-blue-700 mb-1">Forensic Asset Tracing Dashboard</h1>
      <p className="text-sm text-gray-600 mb-4">Web3 Watchdogs | Blocksentinel Intel Force</p>

      <Tabs defaultValue="overview" className="w-full">
        <TabsList className="bg-blue-50">
          <TabsTrigger value="overview">Overview</TabsTrigger>
          <TabsTrigger value="transactions">Transactions</TabsTrigger>
          <TabsTrigger value="recovery">Recovery Plan</TabsTrigger>
        </TabsList>

        <TabsContent value="overview">
          <Card className="mt-4">
            <CardContent className="p-4 space-y-2">
              <p><strong>Client:</strong> Erman Cikan</p>
              <p><strong>Wallet Traced:</strong> TJDENsfBJs4RFETt1X1W8wMDc8M5XnJhCe</p>
              <p><strong>Total Estimated Loss:</strong> $200,000</p>
              <p><strong>Status:</strong> 🛡️ Tracing Complete — Awaiting Final Disbursement</p>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="transactions">
          <Card className="mt-4">
            <CardContent className="p-4">
              <h2 className="text-lg font-semibold mb-2">Transaction Timeline</h2>
              <ResponsiveContainer width="100%" height={250}>
                <BarChart data={txData}>
                  <XAxis dataKey="date" />
                  <YAxis />
                  <Tooltip />
                  <Bar dataKey="amount" fill="#2563eb" radius={[4, 4, 0, 0]} />
                </BarChart>
              </ResponsiveContainer>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="recovery">
          <Card className="mt-4">
            <CardContent className="p-4 space-y-2">
              <p><strong>Recovery Outlook:</strong> ✅ Funds secured under cold-chain disbursement process.</p>
              <p><strong>Disbursement Pending:</strong> Client compliance and final verification required.</p>
              <p><strong>Case ID:</strong> BSIF-ERMAN-0725</p>
              <p><strong>Next Steps:</strong> Verification call scheduled. Disbursement credentials under compliance review.</p>
            </CardContent>
          </Card>
        </TabsContent>
      </Tabs>

      <div className="mt-6 flex flex-col md:flex-row justify-between items-center gap-4">
        <Button variant="outline" onClick={() => window.open(shareLink, '_blank')}>
          <Share2 className="w-4 h-4 mr-2" /> Share via Telegram
        </Button>
        <Button className="bg-blue-700 text-white" onClick={downloadReport}>Download PDF Report</Button>
      </div>
    </div>
  );
}
